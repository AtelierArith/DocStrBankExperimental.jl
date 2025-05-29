```
info::ConstCallInfo <: CallInfo
```

この呼び出しの精度は定数情報を使用して改善されました。元の呼び出し情報 `info.call` に加えて、この情報は定数推論の結果 `info.results::Vector{Union{Nothing,ConstResult}}` も保持します。
