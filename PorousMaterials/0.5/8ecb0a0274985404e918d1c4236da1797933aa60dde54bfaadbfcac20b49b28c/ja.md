```
random_insertion!(molecules::Array{Molecule{Frac}, 1}, box::Box, template::Molecule{Cart})
```

シミュレーションボックスに分子を挿入し、必要に応じてランダムな回転を行います。この関数は、ランダムな位置ベクトルを供給して（`insert_w_random_orientation!`）[@ref]を呼び出します。

# 引数

  * `molecules::Array{Molecule{Frac}, 1}`: シミュレーション内の分子を含む配列
  * `box::Box`: 分数座標に使用されるボックス
  * `template::Molecule{Cart}`: 挿入されるタイプの参照分子
