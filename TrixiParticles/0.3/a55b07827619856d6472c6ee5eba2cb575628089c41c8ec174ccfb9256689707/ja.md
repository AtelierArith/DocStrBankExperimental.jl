```
validation_dir()
```

TrixiParticles.jlに付属する検証ファイルが格納されているディレクトリを返します。TrixiParticlesが通常のパッケージとしてインストールされている場合（`]add TrixiParticles`を使用）、これらのファイルは読み取り専用であり、*変更してはいけません*。利用可能なファイルを見つけるには、例えば`readdir`を使用します。

[Trixi.jl](https://github.com/trixi-framework/Trixi.jl)からコピーしました。

# 例

```@example
readdir(validation_dir())
```
