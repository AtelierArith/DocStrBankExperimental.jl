```
mj_loadXML(filename, vfs, error, error_sz)
```

MJCFまたはURDF形式のXMLファイルを解析し、コンパイルして低レベルのモデルを返します。vfsがNULLでない場合、ディスクから読み込む前にvfs内のファイルを検索します。errorがNULLでない場合、error_szのサイズを持っている必要があります。
