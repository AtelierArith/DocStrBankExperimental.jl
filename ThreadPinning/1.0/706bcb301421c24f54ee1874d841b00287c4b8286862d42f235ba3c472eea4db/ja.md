```
openblas_getcpuid(; threadid)
```

指定された `threadid` の OpenBLAS スレッドが実行されている CPU スレッドの ID を **そのアフィニティに従って** 取得します。

**注意:** OpenBLAS スレッドが以前にピン留めされていない場合、この関数はエラーになります。なぜなら、アフィニティマスクはデフォルトで単一の CPU スレッドを超えるためです。
