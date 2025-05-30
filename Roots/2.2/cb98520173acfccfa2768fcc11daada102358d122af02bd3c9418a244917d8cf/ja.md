```
solve!(P::ZeroProblemIterator)
solve(fx::ZeroProblem, [M], [N]; p=nothing, kwargs...)
init(fx::ZeroProblem, [M], [N];
     p=nothing,
     verbose=false, tracks=NullTracks(), kwargs...)
```

`ZeroProblem`または`ZeroProblemIterator`を通じて指定されたスカラー値の単変数関数のゼロを`CommonSolve`インターフェースを使用して解決します。

`M`と`N`のデフォルトは`ZeroProblem`に依存します：`x0`が数値であれば、`M=Secant()`および`N=AlefeldPotraShi()`が使用されます（`Order0`）；`x0`が`2`（またはそれ以上の値）を持つ場合、それはブレッキング区間であると見なされ、`M=AlefeldPotraShi()`が使用されます。

このインターフェースに関与するメソッドは次のとおりです：

  * `ZeroProblem`：関数（または関数群）と初期推定を指定するために使用されます
  * `solve`：`ZeroProblem`内のゼロを解決するために使用されます

後者は、独立して役立つ以下を呼び出します：

  * `init`：解法のメソッド、デフォルトの許容誤差への調整、およびステップをログに記録するかどうかの指定でイテレータを初期化します。
  * `solve!`：収束するまで反復します。

問題が解決できない場合、`find_zero`のようなエラーではなく`NaN`を返します。ゼロの割り当てについてテスト済みです。

## 例：

```jldoctest find_zero
julia> using Roots

julia> fx = ZeroProblem(sin, 3)
ZeroProblem{typeof(sin), Int64}(sin, 3)

julia> solve(fx)
3.141592653589793
```

または、イテラブルが必要な場合

```jldoctest find_zero
julia> problem = init(fx);

julia> solve!(problem)
3.141592653589793
```

キーワード引数を使用してデフォルトの許容誤差を調整できます。

```jldoctest find_zero
julia> solve(fx, Order5(); atol=1/100)
3.1425464815525403
```

上記は次のように等価です：

```jldoctest find_zero
julia> problem = init(fx, Order5(), atol=1/100);

julia> solve!(problem)
3.1425464815525403
```

キーワード引数`p`は、解決すべき関数がその第2位置引数にパラメータに依存する場合（例：`f(x, p)`）に使用できます。例えば

```jldoctest find_zero
julia> f(x,p) = exp(-x) - p # p = exp(-x)を解く
f (generic function with 1 method)

julia> fx = ZeroProblem(f, 1)
ZeroProblem{typeof(f), Int64}(f, 1)

julia> solve(fx; p=1/2)  # log(2)
0.6931471805599453
```

これは推奨されます。関数が変更されるため再コンパイルはありません。ブロードキャスティングで使用する場合、`p`は最後の位置引数でもかまいません。

`init`の引数`verbose=true`は、ステップをログに記録するよう指示します；

イテレータインターフェースは、`solve`に2つのメソッドが渡されたときに使用されるハイブリッドソリューションの作成を可能にします。例えば、これは本質的にハイブリッドデフォルトが構築される方法です：

```jldoctest find_zero
julia> function order0(f, x)
           fx = ZeroProblem(f, x)
           p = init(fx, Roots.Secant())
           xᵢ,st = ϕ = iterate(p)
           while ϕ !== nothing
               xᵢ, st = ϕ
               state, ctr = st
               fᵢ₋₁, fᵢ = state.fxn0, state.fxn1
               if sign(fᵢ₋₁)*sign(fᵢ) < 0 # ブレッキングをチェック
                   x0 = (state.xn0, state.xn1)
                   fx′ = ZeroProblem(f, x0)
                   p = init(fx′, Bisection())
                   xᵢ = solve!(p)
                   break
               end
               ϕ = iterate(p, st)
           end
           xᵢ
       end
order0 (generic function with 1 method)

julia> order0(sin, 3)
3.141592653589793
```
