#个人笔记
### QT读取中文文件乱码解决方案
QFile file("xxxx.txt");  
QTextStream stream(file,QIODevice::ReadOnly);  
stream.setCodeC( QTextCodec::codecForName("GB2312") );  
stream.readAll(); 

### 字符转换
char转wchar  unicode mbtowc

### vs c++字符编码问题
##1.源码文件是UTF8编码
wchar_t wch = _T('陈');//unicode
std::cout << std::hex << wch << std::endl;
wchar_t wch1 = L'陈';//unicode
std::cout << std::hex << wch1 << std::endl;
wchar_t wch2 = '陈';//GBK
std::cout << std::hex << wch2 << std::endl;

##QString和CString都采用的是unicode编码

##5、QT MFC char*传递乱码问题
QString str = "陈";
QTextCodec *pCodec = QTextCodec::codecForName( "GBK" );
QByteArray data = pCodec->fromUnicode( str );
data.data()


### stl正则表达式
stl正则表达式试中regex_search匹配部分字符就行，regex_match需要完全匹配
