```
modeshape(model::Bar, kn, x, bc = :CC)
modeshape(model::Rod, kn, x, bc = :CC)
modeshape(model::Strings, kn, x, bc = :CC)
modeshape(model::Beam, kn, x, bc = :SS)
```

縦のまたはねじりのバーの質量正規化モード形状を計算します

**入力**

  * `model`: バーデータを含む構造
  * `kn`: モーダル波数の配列
  * `x`: モード形状の計算点の座標
  * `bc`: 境界条件

      * すべてのOneDStructureの場合

          * `:CC`: クランプ - クランプ
          * `:CF`: クランプ - 自由
          * `:FF`: 自由 - 自由
      * ビームの場合

          * `:SS`: 単純支持 - 単純支持
          * `:SC`: 単純支持 - クランプ
          * `:SF`: 単純支持 - 自由

**出力**

  * `ϕ`: 質量正規化モード形状
