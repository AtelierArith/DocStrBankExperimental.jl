```
spgbox!(f, g!, x::AbstractVecOrMat; lower=..., upper=..., options...)
```

初期点 `x` から始めて関数 `f` を最小化します。勾配を計算する関数 `g!` が与えられます。`f` は `f(x)` の形式で、`g!` は `g!(g,x)` の形式でなければなりません。ここで `g` は修正される勾配ベクトルです。`x` ベクトルを修正し、見つかった最良の解を含むことになります（非変異的な代替手段については `spgbox` を参照してください）。

オプションの下限および上限のボックス境界は、オプション引数 `lower` と `upper` を使用して提供できます。これらは第4および第5の引数として、またはキーワードパラメータとして提供できます。

`x` に見つかった最良の解と最終的な目的関数 `f` を含む `SPGBoxResult` 型の構造体を返します。

また、関数値と勾配を計算する単一の関数を提供することもできます。次のように使用します：

```
spgbox(fg!, x; lower=..., upper=..., options...)
```

`fg!` は `fg!(g,x)` の形式でなければならず、ここで `x` は現在の点で、`g` は勾配を格納する配列です。そして、関数値を返さなければなりません。   

# 例

```julia-repl
julia> f(x) = x[1]^2 + x[2]^2

julia> function g!(g,x)
           g[1] = 2*x[1]
           g[2] = 2*x[2]
       end
```

## 制約なし

```julia-repl
julia> x = [1.0, 2.0]

julia> spgbox!(f,g!,x)

 SPGBOX RESULT: 

 収束達成。 

 最終目的関数値 = 0.0
 最良点のサンプル = Vector{Float64}[ 0.0, 0.0]
 投影勾配ノルム = 0.0

 イテレーション数 = 3
 関数評価数 = 3
```

## 制約あり

```julia-repl
julia> x = [3.0, 4.0]

julia> spgbox!(f,g!,x,lower=[2.,-Inf])

 SPGBOX RESULT: 

 収束達成。

 最終目的関数値 = 4.0
 最良点のサンプル = Vector{Float64}[ 2.0, 0.0]
 投影勾配ノルム = 0.0

 イテレーション数 = 1
 関数評価数 = 1
```

## 関数と勾配を計算する単一の関数を使用

```julia-repl
julia> function fg!(g,x)
           g[1] = 2*x[1]
           g[2] = 2*x[2]
           fx = x[1]^2 + x[2]^2
           return fx
       end
fg! (generic function with 1 method)

julia> x = [1.0, 2.0];

julia> spgbox(fg!,x)

 SPGBOX RESULT: 

 収束達成。 

 最終目的関数値 = 0.0
 最良点のサンプル = Vector{Float64}[ 0.0, 0.0]
 投影勾配ノルム = 0.0

 イテレーション数 = 3
 関数評価数 = 3
```
