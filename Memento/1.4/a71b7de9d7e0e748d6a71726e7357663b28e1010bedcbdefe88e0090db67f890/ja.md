```
setlevel!(f::Function, logger::Logger, level::AbstractString; recursive=false)
```

関数 `f` の実行中にロガーがログを記録するレベルを一時的に変更します。
