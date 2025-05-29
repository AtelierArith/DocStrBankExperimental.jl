```
SegmentRef
```

`Segment`への参照と、この`Segment`がどの`ObjectHandle`から来ているかの参照を提供します。これは、ユーザーがオブジェクトファイル内のセグメントと対話するための主要な方法であるべきです。利用可能なAPI操作のリストは以下に示されており、サブクラスが実装しなければならないメソッドは強調表示されています。これは`Segment`オブジェクトAPIと重複していることに注意してください。これは、多くのメソッドが使いやすさのために基盤となる`Segment` API呼び出しへのパススルーであるため、意図的なものです。

### 作成:

  * *SegmentRef()*

### ユーティリティ

  * *deref()*
  * *Segments()*
  * handle()

### フォーマット固有のプロパティ:

  * *segment_name()*
  * *segment_number()*
  * segment_offset()
  * segment*file*size()
  * segment*memory*size()
  * segment_address()
