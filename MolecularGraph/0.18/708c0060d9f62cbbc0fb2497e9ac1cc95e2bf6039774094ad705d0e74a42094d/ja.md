```
simulate_massspec(peaks::Vector{Tuple{Float64,Float64}};
    resolution=10000, rate=0.01) -> Matrix{Float64}
simulate_massspec(mol::MolGraph;
    threshold=0.001, resolution=10000, rate=0.01) -> Matrix{Float64}
```

質量スペクトルをシミュレートした行列を返します（次元1：データポイント、次元2：質量と強度）。

ピークは原子の同位体組成から計算されたものであり（断片化のシミュレーションを意図したものではありません）。

# 使用法（Plot.jlを使用）

```julia
using MolecularGraph
using Plots
gr()
Plots.GRBackend()

mol = smilestomol("CCO")
data = simulatemassspec(mol)
plot(
    data[:, 1], data[:, 2],
    leg=false, xlabel = "質量", ylabel = "強度"
)
```
