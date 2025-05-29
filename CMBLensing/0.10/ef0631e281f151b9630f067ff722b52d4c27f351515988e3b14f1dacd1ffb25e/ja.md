```
ProjEquiRect(; Ny::Int, Nx::Int, θspan::Tuple, φspan::Tuple,         T=Float32, storage=Array)
ProjEquiRect(; θ::Vector, φ::Vector, θedges::Vector, φedges::Vector, T=Float32, storage=Array)
```

等距矩形投影オブジェクトを構築します。投影は次のいずれかで指定できます：

  * ピクセル数 `Ny` と `Nx`（それぞれ `θ` と `φ` の角度方向に対応）およびこれらの方向のフィールドのラジアンでの範囲 `θspan` と `φspan`。範囲タプルの順序は重要ではなく、どちらの順序でも同じフィールドを指します。なお、範囲は外側のピクセルエッジ間のフィールドサイズに対応し、ピクセルの中心からではありません。この投影で `Cℓ_to_Cov` を呼び出したい場合、`φspan` は 2π の整数倍でなければなりませんが、そうでない場合でも他の機能は利用可能です。
  * ピクセルの中心とピクセルエッジの手動リスト `θ`、`φ`、`θedges`、`φedges`。
