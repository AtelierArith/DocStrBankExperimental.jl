```
is_distorted = distortion(molecule, ref_molecule, box; 
                          atol=1e-12, throw_warning=true)
```

分子が参照分子に対して歪んでいるかどうかを、原子と電荷の座標のペアワイズ距離比較を通じて判断します。

# 引数

  * `molecule::Molecule{Frac}`: 比較したい分子
  * `ref_molecule::Molecule{Frac}`: 参照分子
  * `box::Box`: 分数座標に使用されるボックス
  * `atol::Float64=1e-12`: 距離比較のための絶対許容誤差
  * `throw_warning::Bool=true`: 歪みがある場合に警告を発行する

# 戻り値

  * `is_distorted::Bool`: 参照分子に対して歪みがある場合はtrue
