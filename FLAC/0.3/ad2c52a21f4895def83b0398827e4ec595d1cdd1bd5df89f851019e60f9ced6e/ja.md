```
initfile!(dd::StreamDecoderPtr, fnm::String; wcallback=debug_wcallback_c,
    mcallback=debug_mcallback_c, ecallback=debug_ecallback_c, client_data=nothing)
```

`StreamDecoderPtr`である`dd`を初期化し、FLACファイル`fnm`を読み取ります。

この関数は、ユーザーがデフォルトのコールバック関数をオーバーライドすることを許可します。
