```
superkick(;v=0.2, χ=0.99, PNOrder=typemax(Int))
superkick(;v=0.2, chi=0.99, PNOrder=typemax(Int))
```

「superkick」構成でブラックホールバイナリを構築します。

これは、[Campanelli et al. (2007)](https://arxiv.org/abs/gr-qc/0701164)によって最初に発表されたシナリオで、軌道面で反対方向に向けられた同じ大きさのスピンを持つ等質量のブラックホールを含みます。この構成は、バイナリがどの部分の軌道にいるかに応じて、$+z$または$-z$方向に沿った重力波の線運動量の大きな非対称放出を生じさせます。システムが合体するタイミングによっては、残骸が巨大な反動速度を獲得することがあります。

（その反動速度はもちろん、合体の詳細に依存し、ポストニュートン近似では記述できません。したがって、残骸に関する有用な情報を導出するためにPN手法を実際に使用することはできません。）

「superkick」という名前は、さらに大きな反動速度を達成できるシステムのクラスが文献に登場する前に現れました：そのようなシステムについては[`hangup_kick`](@ref)を参照してください。

# 例

```julia-repl
julia> pnsystem = superkick(v=0.1)
BBH{Vector{Float64}, 9223372036854775805//2}([0.5, 0.5, 0.99, 0.0, 0.0, -0.99, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 0.1, 0.0])

julia> inspiral = orbital_evolution(pnsystem);

julia> inspiral[:v, 1]
0.1

julia> absvec(PostNewtonian.χ⃗₁(inspiral[1]))
0.99
```
