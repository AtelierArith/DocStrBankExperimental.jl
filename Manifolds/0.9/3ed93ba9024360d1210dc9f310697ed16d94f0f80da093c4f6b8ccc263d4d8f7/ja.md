```
project(M::ProbabilitySimplex, p)
```

埋め込みから[`ProbabilitySimplex`](@ref) `M`への`p`の射影。式は次のようになります。

$$
\operatorname{proj}_{Δ^n}(p) = \frac{1}{⟨\mathbb 1,p⟩}p,
$$

ここで、$\mathbb 1 ∈ ℝ$は1のベクトルを示します。この射影は、$p$が正のエントリを持つ場合にのみ定義されることに注意してください。
