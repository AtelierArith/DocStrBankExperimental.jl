```
examples_dir()
```

DispersiveShallowWater.jlに付属する例ファイルが格納されているディレクトリを返します。DispersiveShallowWaterが通常のパッケージとしてインストールされている場合（`]add DispersiveShallowWater`を使用）、これらのファイルは読み取り専用であり、*変更してはいけません*。利用可能なファイルを見つけるには、例えば`readdir`を使用します。

[Trixi.jl](https://github.com/trixi-framework/Trixi.jl)からコピーしました。

# 例

```@example
readdir(examples_dir())
```
