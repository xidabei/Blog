####Study Bitcoin####
最近在学习《精通比特比》一书，其中个有一段代码是C++，需要用到libbitcoin库，为此开启了安装libbitcoin库的征程。
#####Install the libbitcoin#####
这是我最终编译libbitcoin的命令，每个参数都缺失都会有不同的错误产生。描述如下：

sudo ./install.sh PKG_CONFIG_PATH=/usr/local/lib/pkgconfig --build-boost --prefix=/opt/libbitcoin --with-boost-libdir=/usr/local/lib

如果缺少`PKG_CONFIG_PATH=/usr/local/lib/pkgconfig`, 
错误为`can not find libsecp256k1.so`

如果缺少`--prefix=/opt/libbitcoin`,
错误如下：
<pre><code>CXXLD    examples/libbitcoin_examples
src/.libs/libbitcoin.so: undefined reference to `boost::re_detail_106100::put_mem_block(void*)'
src/.libs/libbitcoin.so: undefined reference to `boost::re_detail_106100::get_default_error_string(boost::regex_constants::error_type)'
src/.libs/libbitcoin.so: undefined reference to `boost::re_detail_106100::cpp_regex_traits_implementation<char>::transform_primary(char const*, char const*) const'
src/.libs/libbitcoin.so: undefined reference to `boost::re_detail_106100::get_mem_block()'
src/.libs/libbitcoin.so: undefined reference to `boost::re_detail_106100::verify_options(unsigned int, boost::regex_constants::_match_flags)'
src/.libs/libbitcoin.so: undefined reference to `boost::re_detail_106100::raise_runtime_error(std::runtime_error const&)'
src/.libs/libbitcoin.so: undefined reference to `boost::re_detail_106100::cpp_regex_traits_implementation<char>::transform(char const*, char const*) const'
src/.libs/libbitcoin.so: undefined reference to `boost::re_detail_106100::perl_matcher<__gnu_cxx::__normal_iterator<char const*, std::string>, std::allocator<boost::sub_match<__gnu_cxx::__normal_iterator<char const*, std::string> > >, boost::regex_traits<char, boost::cpp_regex_traits<char> > >::construct_init(boost::basic_regex<char, boost::regex_traits<char, boost::cpp_regex_traits<char> > > const&, boost::regex_constants::_match_flags)'
collect2: error: ld returned 1 exit status
make: *** [examples/libbitcoin_examples] Error 1
</code></pre>

如果缺少` --with-boost-libdir=/usr/local/lib`, 
错误为：
`configure: error: Could not link against boost_system`
以上错误具体原因没有深纠，搞了好几天终于搞定，还是很开熏的～～

