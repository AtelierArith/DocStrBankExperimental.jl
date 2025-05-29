```
MCCGA(;N, maxsamples)
```

### パラメータ:

  * `N` 集団のサイズ。デフォルトは100。
  * `maxsamples` 最大サンプル数。デフォルトは10000。

### 説明

MCCGAメソッドは、実数値最適化問題のための機械コード化された遺伝的アルゴリズムを実装しています。このアルゴリズムは、コンパクト遺伝的アルゴリズムの概念に基づいていますが、IEEE-754浮動小数点エンコーディング標準を使用した機械コード化された表現を用いています。アルゴリズムの最初の段階では、`maxsamples`の数のサンプルが関数のドメインの範囲内で生成されます。このプロセスは、IEEE-754表現の各ビットの確率ベクトルを取得するために必要です。従来のCGAでは、初期の確率ベクトルは0.5の定数確率を使用して生成されますが、MCCGAでは、i番目のビットが1の値を持つ確率は関数のドメインに依存します。第二のステップでは、再びIEEE-754ビットを用いてCGA検索が行われます。CGAは解の集団を使用せず、単一の確率ベクトルを使用するため、パラメータ`N`は実際には解の数を意味しません。代わりに、各イテレーションでの突然変異の量、例えば1/Nを意味します。最後の段階では、微調整のために局所探索が行われます。この実装では、フック＆ジーブスの直接探索アルゴリズムが使用されています。

### 参考文献

  * Moser, Irene. "Hooke-Jeeves Revisited." 2009 IEEE Congress on Evolutionary Computation. IEEE, 2009.
  * Harik, G. R., Lobo, F. G., & Goldberg, D. E. (1999). The compact genetic algorithm. IEEE transactions on evolutionary computation, 3(4), 287-297.
  * Satman, M. H. & Akadal, E. (2020). Machine Coded Compact Genetic Algorithms for Real Parameter Optimization Problems . Alphanumeric Journal , 8 (1) , 43-58 . DOI: 10.17093/alphanumeric.576919
  * Mehmet Hakan Satman, Emre Akadal, Makine Kodlu Hibrit Kompakt Genetik Algoritmalar Optimizasyon Yöntemi, Patent, TR, 2022/01, 2018-GE-510239

### 例

```jldoctest

julia> f, bounds, solutions = Metaheuristics.TestProblems.rastrigin();

julia> result = optimize(f, bounds, MCCGA())

+=========== RESULT ==========+
  iteration: 42833
    minimum: 0
  minimizer: [-5.677669786379456e-17, 2.7942451898022582e-39, -3.60925916059986e-33, -6.609510861086017e-34, 2.998586759675011e-32, -1.8825832500775007e-38, -3.0729484147585938e-31, 1.7675578057632446e-38, 5.127944874215823e-16, 1.9623770480857484e-19]
    f calls: 86404
 total time: 3.2839 s
+============================+
```

### 明示的な例

```jldoctest

julia> using Metaheuristics                                                                                         
                                                              
julia> f(x::Vector{Float64})::Float64 = (x[1]-pi)^2 + (x[2]-exp(1))^2                                                                                
                                                              
julia> bounds = [ -500.0  -500.0;                                    
                   500.0  500.0]                                      

julia> result = Metaheuristics.optimize(f, bounds, MCCGA())

+=========== RESULT ==========+
  iteration: 2974
    minimum: 1.80997e-09
  minimizer: [3.1416284249228976, 2.7183048585824263]
    f calls: 6012
 total time: 1.5233 s
stop reason: Other stopping criteria.
+============================+
```
