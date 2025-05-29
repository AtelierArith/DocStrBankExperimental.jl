```
examples_dir()
```

Trixi.jlに付属する例ファイルが格納されているディレクトリを返します。Trixi.jlが通常のパッケージとしてインストールされている場合（`]add Trixi`を使用）、これらのファイルは読み取り専用であり、*変更しないでください*。利用可能なファイルを見つけるには、例えば`readdir`を使用します：

# 例

```@example
readdir(examples_dir())
```
