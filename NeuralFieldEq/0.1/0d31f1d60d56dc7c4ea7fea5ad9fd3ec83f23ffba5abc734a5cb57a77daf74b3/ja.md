```
solveNFE(problem,saveat)
```

# 引数:

  * `problem :: ProbOutput1D`: Input1D構造体を使用したprobNFEの出力
  * `problem :: ProbOutput2D`: Input2D構造体を使用したprobNFEの出力
  * `saveat  :: AbstractVector`: 解が保存される瞬間を含むベクトル

saveatの瞬間で保存されたNFEの解を含む構造体を返します。この構造体には、解をプロットするのに役立つフィールドとして`x`、`y`、`saveat`があります。

# 例

```julia-repl
julia> # 2Dの例
julia> saveat = [5.0,20.0]
julia> sol    = solveNFE(prob,saveat) # t=5およびt=20で保存された決定論的解
julia> sol(20.0) # t=20での解
julia> x = sol.x # x方向の空間ベクトル 
julia> y = sol.y # y方向の空間ベクトル
julia> using Plots
julia> plot(x,y,sol(20.0),st=:surface,title="t=20での解") # sol(20.0)のサーフェスプロット
```

神経場が1D/2Dの場合、解はベクトル/行列です。

---

```
solveNFE(problem,saveat,ϵ,np,ξ=0.1)
```

npの軌跡、ノイズレベルϵ、および相関ξのためのNFEの確率的バージョンを解きます。

# 引数:

  * `problem :: ProbOutput1D`: Input1Dを使用したprobNFEの出力
  * `problem :: ProbOutput2D`: Input2Dを使用したprobNFEの出力
  * `saveat  :: AbstractVector`: 解が保存される瞬間を含むベクトル
  * `ϵ       :: Number`: 加法的ノイズのレベル
  * `np      :: Integer`: シミュレーションの数
  * `ξ       :: AbstractFloat=0.1`: 空間相関パラメータ

saveatの瞬間で保存されたNFEの平均解と軌跡を含む構造体を返します。

# 例

```julia-repl
julia> # ノイズレベル0.01で100回シミュレーションされたt=5,20で保存された確率的解。
julia> sol_sto = solveNFE(prob,saveat,0.01,100)
julia> sol_sto(20.0,4) # t=20での4番目の経路
julia> sol_sto(5.0)    # t=20での平均解
```
