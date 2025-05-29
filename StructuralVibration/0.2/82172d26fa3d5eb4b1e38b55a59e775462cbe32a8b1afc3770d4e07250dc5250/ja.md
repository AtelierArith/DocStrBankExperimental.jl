```
modefreq(model::Bar, fmax, bc = :CC)
modefreq(model::Rod, fmax, bc = :CC)
modefreq(model::Strings, fmax, bc = :CC)
modefreq(model::Beam, fmax, bc = :SS)
```

自然周波数を最大周波数 fmax まで計算します。

**入力**

  * `model`: バーのデータを含む構造体
  * `fmax`: モードシェイプを計算するための最大周波数 [Hz]
  * `bc`: 境界条件

      * すべての OneDStructure に対して

          * `:CC`: クランプ - クランプ
          * `:CF`: クランプ - 自由
          * `:FF`: 自由 - 自由
      * ビームの場合

          * `:SS`: 単純支持 - 単純支持
          * `:SC`: 単純支持 - クランプ
          * `:SF`: 単純支持 - 自由

**出力**

  * `ωn`: ωmax = 2π*fmax まで計算された自然周波数 [Hz]
  * `kn`: モーダル波数のベクトル
