```
Profile(countmat, omicsname, var, obs; varindex=:genesymbol, obsindex::Symbol=:barcode,
        T=float(eltype(countmat)))
```

`AnnotatedProfile`を内部に持つ`OmicsProfile`を確立するためのコンストラクタです。

# 引数

  * `countmat`: 指定されたオミクスのカウント行列で、キー`:count`に設定されます。
  * `omicsname::Symbol`: 指定された`OmicsProfile`の名前。
  * `var::DataFrame`: 特徴または変数のメタ情報を含むデータフレーム。
  * `obs::DataFrame`: 観測のメタ情報を含むデータフレーム。
  * `varindex::Symbol`: データフレーム`var`のインデックス。
  * `obsindex::Symbol`: データフレーム`obs`のインデックス。
  * `T`: `countmat`の要素型。
