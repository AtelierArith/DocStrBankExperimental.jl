```
function ortho2inv(x, y, ϕ1, λ0)
```

逆ステレオ正射影投影は (ϕ1, λ0) を中心とします。平面上の点 (x, y) が与えられ、x ∈ [-1, 1]、y ∈ [-1, 1] の場合、(Bool, Number, Number) 型の 3 タプルを返します。ブール値は (x, y) が地図内にあるかどうかを指定し (true) またはない場合 (false)、2 番目と 3 番目の引数はラジアンでの緯度と経度です。
