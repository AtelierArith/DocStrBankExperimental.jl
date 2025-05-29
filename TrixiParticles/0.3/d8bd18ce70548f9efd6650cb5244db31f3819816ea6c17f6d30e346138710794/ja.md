```
examples_dir()
```

TrixiParticles.jlに付属するサンプルファイルが格納されているディレクトリを返します。TrixiParticlesが通常のパッケージとしてインストールされている場合（`]add TrixiParticles`を使用）、これらのファイルは読み取り専用であり、*変更してはいけません*。利用可能なファイルを見つけるには、例えば`readdir`を使用します。

[こちら](https://github.com/trixi-framework/Trixi.jl)からコピーしました。

# 例

```jldoctest; output = false, filter = r"\d+-element Vector.*"s
readdir(examples_dir())

# output
7-element Vector{String}:
 [...] (残りはフィルター条件によって無視されます)
```
