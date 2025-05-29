```
prompt_and_parse(pp::Nothing) = (;abort=false, argpairs = emptyargs())
prompt_and_parse(pp::ArgumentParser) → (;abort, argpairs)
```

プロンプトを表示し、ユーザーからの入力を読み取り、解析します。詳細についてはドキュメントのフローダイアグラムを参照してください。

# 引数

  * `pp::Union{Nothing, ArgumentParser}`: コマンドライン引数用のArgumentParser。

# 戻り値のNamedTuple

  * `abort::Bool`
  * `argpairs`: ペアのベクター `argname::Symbol => argvalue::Any`

関数 `prompt_and_parse` は公開されており、エクスポートされていません。
