ギリシャ語の文学的なためのGreekOrthographyの`augment`関数の実装。

```julia
augment(ortho; s)

```

注: `augment`は結果の文字列からすべてのアクセントを削除します。

# パラメータ

  * `ortho` `AtticOrthography`のインスタンス
  * `s` 増強するためのオプションの文字列。含まれていない場合、関数は音節増強のためのデフォルトの増強文字列を返します（すなわち、子音で始まる動詞形に適用できる文字列）。
