```
mjp_registerPlugin(plugin)
```

プラグインをグローバルに登録します。この関数はスレッドセーフです。同一の mjpPlugin がすでに登録されている場合、この関数は何もしません。同一でない mjpPlugin が同じ名前で既に登録されている場合、mju_error が発生します。2つの mjpPlugins は、すべてのメンバ関数ポインタと数が等しく、名前と属性文字列がすべて同一である場合に同一と見なされますが、文字列への char ポインタは同じである必要はありません。
