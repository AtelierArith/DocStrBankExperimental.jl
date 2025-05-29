1つ以上のデータソースから`Tabulae.Dataset`を作成します。

```julia
dataset(srclist; ortho)

```

# 引数

  * `srclist` Tabulaeデータを含むディレクトリへのフルパスのリスト。
  * `ortho` `LatinOrthographicSystem`のインスタンス; デフォルトは`Latin23`です。
