```
outputs = basic_run(; kwargs...)
```

基本的なAquaCropシミュレーションを実行します。`outputs`変数にはシミュレーションの結果を含む最終データフレームがあります。

現在許可されている`runtype`は`NormalFileRun`または`TomlFileRun`です。

`NormalFileRun`は、AquaCrop Fortranのようにファイルからの入力を使用します（AquaCrop.jl/test/testcaseを参照）。

`TomlFileRun`は、TOMLファイルからの入力を使用します（AquaCrop.jl/test/testcase/TOML_FILESを参照）。

`outputs[:dayout]`で日次結果を、`outputs[:harvestsout]`で各収穫の結果を、`outputs[:seasonout]`でシーズン全体の結果を、`outputs[:evaldataout]`で評価のための情報を、`outputs[:logger]`でロガー情報を確認できます。
