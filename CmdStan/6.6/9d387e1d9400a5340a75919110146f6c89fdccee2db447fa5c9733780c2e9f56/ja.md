# `rel_path_cmdstan`

CmdStan.jlのsrcディレクトリを使用した相対パス。このアプローチは[DynamicHMCExamples.jl](https://github.com/tpapp/DynamicHMCExamples.jl)からコピーされています。

### データサブディレクトリにアクセスする例

```julia
rel_path_cmdstan("..", "data")
```
