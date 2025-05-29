```
proc_ARGS(pp0::Nothing) = (;abort=false, argpairs = emptyargs())
proc_ARGS(pp0::ArgumentParser) → (;abort, argpairs)
```

コマンドラインからスクリプトに提供された引数を読み取り、解析します。詳細については、ドキュメントのフローダイアグラムを参照してください。

# 引数

  * `pp0::Union{Nothing, ArgumentParser}`: コマンドライン引数用のArgumentParser。

# 返されるNamedTuple

  * `abort::Bool`
  * `argpairs`: ペアのベクター `argname::Symbol => argvalue::Any`

関数 `proc_ARGS` は公開されており、エクスポートされていません。
