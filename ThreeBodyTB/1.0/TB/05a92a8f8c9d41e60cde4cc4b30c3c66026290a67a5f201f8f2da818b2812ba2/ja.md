```
function calc_bands(tbc::tb_crys, kpoints::Array{Float64,2}; spin=1)
```

k点配列からのバンド構造を計算します。固有値を返します。

# 引数

  * `tbc::tb_crys` - タイトバインディングオブジェクト
  * `kpoints::Array{Float64,2}` - k点配列。例: `[0.0 0.0 0.0; 0.0 0.0 0.1]`
  * `spin::Int` - 磁気の場合のスピン成分（1または2）、非スピンの場合は1のみ。
