```
openblas_unpinthread(; threadid)
```

指定された `threadid` の OpenBLAS スレッドのピンを外し、そのアフィニティマスクをすべてのユニティに設定します。その後、OS は OpenBLAS スレッドをある CPU スレッドから別のスレッドに移動することができます。
