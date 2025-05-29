```
get_permittivity(mat::Material,λ)
get_permittivity(mat::Material,λ,index)
```

指定された波長と座標方向に対する材料モデルオブジェクトの誘電率を返します。

# 引数

  * `mat` : 材料オブジェクト
  * `λ` : 自由空間の波長
  * `index` : オプション、異方性材料の座標方向を指定します

# 出力

  * `ε` : 指定された波長と座標方向に対する複素スカラー誘電率値
