```
ObjectHandle
```

オブジェクトファイルへのアクセスを提供する基本型です。利用可能なAPI操作のリストは以下に示されており、サブクラスが実装しなければならないメソッドは強調表示されています。「実装しなければならない」というのは少し誤解を招く表現であり、オブジェクトファイルがこのAPIの特定の部分を必要としない場合（例えば、`COFF`ファイルには`Segment`の概念がない）、そのAPIの部分が未定義のままにされると、ユーザーがそのAPIの部分を使用するメソッドを呼び出そうとしたときにエラーが発生します（上記の例では、ユーザーが`Segments(oh)`を呼び出すとエラーが発生します。ここで`oh <: COFFHandle`です）。

### 作成

  * *readmeta()*

### IOStreamのような操作:

  * seek()
  * seekstart()
  * skip()
  * startaddr()
  * iostream()
  * position()
  * read()
  * readuntil()
  * eof()
  * unpack()

### フォーマット固有のプロパティ

  * *Platform()*
  * *endianness()*
  * *is64bit()*
  * *isrelocatable()*
  * *isexecutable()*
  * *islibrary()*
  * *isdynamic()*
  * *mangle*section*name()*
  * *mangle*symbol*name()*
  * handle()
  * *header()*
  * *format_string()*

### セクションプロパティ

  * *section*header*offset()*
  * *section*header*size()*
  * *section*header*type()*

### セグメントプロパティ

  * *segment*header*offset()*
  * *segment*header*size()*
  * *segment*header*type()*

### シンボルプロパティ

  * *symtab*entry*offset()*
  * *symtab*entry*size()*
  * *symtab*entry*type()*

### その他

  * *path()*
  * show()
  * find_library()
  * find_libraries()
