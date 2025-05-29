```
SectionRef
```

`Section`への参照と、この`Section`がどの`ObjectHandle`から来ているかの参照を提供します。これは、ユーザーがオブジェクトファイル内のセクションと対話するための主要な方法であるべきです。利用可能なAPI操作のリストは以下に示されており、サブクラスが実装しなければならないメソッドは強調表示されています。これは`Section`オブジェクトAPIと重複していることに注意してください。これは、多くのメソッドが使いやすさのために基盤となる`Section` API呼び出しへのパススルーであるため、意図的なものです。

### 作成:

  * *SectionRef()*

### ユーティリティ

  * *deref()*
  * *handle()*
  * *Sections()*

### IOのような操作:

  * read()
  * seekstart()
  * seek()
  * eof()

### フォーマット固有のプロパティ:

  * section_name()
  * *section_number()*
  * section_type()
  * section_size()
  * section_offset()
  * section_address()
