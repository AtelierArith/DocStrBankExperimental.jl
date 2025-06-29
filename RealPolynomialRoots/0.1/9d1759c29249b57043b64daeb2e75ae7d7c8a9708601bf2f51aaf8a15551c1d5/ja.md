```
ANewDsc(p; root_bound=(lowerbound(p), upperbound(p)), max_depth=96)
refine_interval(p, a, b, L)
refine_roots(st::State)
```

実数根の孤立区間を見つけるためのメソッドで、`p`に格納された係数によって指定された平方自由多項式です。

  * `p`: **平方自由**多項式の多項式係数、`[a₀, a₁, …, aₙ]`。
  * `root_bound`: 実数根の下限と上限。

`State`インスタンスを返し、以下のコンポーネントを持ちます：

  * `Isol`は孤立区間を保持します。`State`オブジェクトを反復処理すると、`Isol`を反復処理します。
  * `Unresolved`は未解決の区間を保持します。表示メソッドはそのような区間の存在を警告します。

アルゴリズムにはランダムなステップが含まれており、出力に小さな変動をもたらします。

例：

```
julia> using RealPolynomialRoots

julia> ps = [-1, 254, -16129, 0, 0, 0, 0, 1] # 近くに2つの根を持つミニョット多項式
8-element Vector{Int64}:
     -1
    254
 -16129
      0
      0
      0
      0
      1

julia> st = ANewDsc(ps)
孤立区間が3つ見つかりました：
[3.5…, 7.25…]₅₃
[0.00787401594698…, 0.00787401779189…]₆₃
[0.00787401419348…, 0.00787401594698…]₆₃

julia> ps = [3628800, -10628640, 12753576, -8409500, 3416930, -902055, 157773, -18150, 1320, -55, 1]; # πᵢ₌₁¹⁰ (x-i)

julia> st = ANewDsc(ps)
孤立区間が10個見つかりました：
[9.25…, 10.2…]₅₃
[8.5…, 9.25…]₅₃
[7.5…, 8.5…]₅₃
[6.5…, 7.5…]₅₃
[5.62…, 6.5…]₅₃
[4.88…, 5.62…]₅₃
[3.0…, 4.75…]₅₃
[2.19…, 3.0…]₅₃
[1.28…, 2.19…]₅₃
[-0.5…, 1.31…]₅₃

julia> ps =[ # from https://discourse.julialang.org/t/root-isolation-of-real-rooted-integer-polynomials/51421/1
                      942438915208811912419937422298363203125
                   164182217245953398816894035758761902846875
                  4584900574568933770264468813466870772155175
                 48995332393110515074735075708247882042540865
                266674183150777010544241114017741621823207005
                852443280934837985352088128423887894438557515
               1738546146302892245736990844587487000484756535
               2381558158813900978436742173305983349418813145
               2262003889258248241081177038309445610985409335
               1516025051068561122302699855213604175083575145
                720810987764796866354279087485114863858085005
                241341213302325116160821160849326697595681275
                 55563538585119205063994483187179167406616375
                  8363912237256094118085070946083688310200625
                   740493466743082745510080711751444519503125
                    29215606371473169285018060091249259296875];

julia> ANewDsc(ps)
孤立区間が15個見つかりました：
[-0.01617…, 0.0531…]₂₅₆
[-0.08643…, -0.01617…]₂₅₆
[-0.2285…, -0.08643…]₂₅₆
[-0.3711…, -0.2285…]₂₅₆
[-0.6562…, -0.3672…]₂₅₆
[-0.9531…, -0.6562…]₂₅₆
[-1.234…, -0.9531…]₂₅₆
[-1.84…, -1.25…]₂₅₆
[-2.125…, -1.812…]₂₅₆
[-2.438…, -2.125…]₂₅₆
[-3.0…, -2.44…]₂₅₆
[-3.281…, -3.031…]₂₅₆
[-3.562…, -3.281…]₂₅₆
[-3.875…, -3.562…]₂₅₆
[-4.188…, -3.875…]₂₅₆
```

## 精緻化

`refine_interval`メソッドは、幅が$2^{-L}$より小さくなるように区間を精緻化するために使用できます。`L`は指定できますが、そうでなければ区間の精度から来ます。

あるいは、`Roots`のようなパッケージを使用することもできます。例えば、`[find_zero(st, I) for I ∈ st]`（ここで`st`は`ANewDsc`によって返された`State`オブジェクトです）。`Float64`値に対して精緻化が望ましく、根の分離が適切である場合、その呼び出しは次のように修正できます：`[find_zero(st, Float64.(I)) for I ∈ st]`。（これは`nextfloat`と`prevfloat`の間で符号が変わる根を生成するはずです。）

## 比較

このアルゴリズムをここでの実装で判断しないでください。この実装は、可能な限りのパフォーマンスではありません。

いくつかの代替手段と比較すると、Hecke.jlの機能（`Hecke._roots`）は**はるかに**優れています。（最後の例は33 ≈ 0.14s/0.0042倍速い）

しかし、他の代替手段と比較すると、この実装は有用と見なされるかもしれません：

```
julia> x = variable(Polynomial);

julia> p = -1 + 254*x - 16129*x^2 + x^15;

julia> ANewDsc(coeffs(p))  # ≈ 0.05秒;
孤立区間が3つ見つかりました：
[0.75…, 4.25…]₅₃
[0.00787401574803149653139…, 0.00787401574803149972047…]₂₁₂
[0.0078740157480314937167…, 0.00787401574803149653139…]₂₁₂

julia> filter(isreal, roots(p)) # はるかに速いが、虚部が~1e-10の2つの根を見逃す
1-element Array{Complex{Float64},1}:
 2.1057742291764914 + 0.0im

julia> filter(isreal, AMRVW.roots(Float64.(coeffs(p)))) # AMRVWを使用。似たように2つの根を見逃す
1-element Array{Complex{Float64},1}:
 2.1057742291764407 + 0.0im

julia> filter(isreal, AMRVW.roots(BigFloat.(coeffs(p)))) # ここではこれが機能する
3-element Vector{Complex{BigFloat}}:
 0.007874015748031494751793842937491860399146218747427882112208862187156603046408902 + 0.0im
 0.007874015748031497374190409031015351762713667398750832139185145345899098824178322 + 0.0im
    2.105774229176482954331883383107195997983004314462374928263620342390986189650864 + 0.0im

julia> filter(isreal, PolynomialRoots.roots(coeffs(p))) # PolynomialRootsを使用。2.105を見逃す？
2-element Array{Complex{Float64},1}:
   0.0078740158234482 + 0.0im
 0.007874015672614794 + 0.0im

julia> IntervalRootFinding.roots(x->p(x), IntervalArithmetic.Interval(0.0, 5.0)) # IntervalRootFinding、IntervalArithmeticを使用
8-element Array{Root{IntervalArithmetic.Interval{Float64}},1}:
 Root([2.10577, 2.10578], :unique)
 Root([0.00787418, 0.00787422], :unknown)
 Root([0.00787403, 0.00787409], :unknown)
[...]

julia> @syms x::real # SymPyを使用

julia> @time  rts = sympy.real_roots(p(x)); # 正しく3つを特定。
  0.003896秒 (518アロケーション: 13.359 KiB)

julia> sympy.N(rts[2]) # 時間がかかる！ (162秒)
0.00787401574803150
```

使用されるアルゴリズムは、次の文献で提示されたアルゴリズムの部分的な実装です：

*Computing Real Roots of Real Polynomials ... and now For Real!* by Alexander Kobel, Fabrice Rouillier, Michael Sagraloff [arXiv](https://arXiv.org/1605.00410); [DOI:](https://doi.org/10.1145/2930889.2930937)。

および

*Computing real roots of real polynomials* Michael Sagraloff, Kurt Mehlhorn [DOI:](https://doi.org/10.1016/j.jsc.2015.03.004)

このアルゴリズムは、Descartesの符号の法則に依存しており、これは多項式`p(x)`の正の実数根の数の上限を与えます。多項式`p((ax+b)/(x+1))`を考慮することによって、`[a,b]`から`[0,∞)`へのマッピングを行い、`[a,b]`内の根の数の上限を見つけることができます。平方自由多項式に対する単純な二分法は、すべての実数根を含むのに十分大きな区間から始め、次に中点で分割し、根が存在しないことがわかったサブ区間を捨て、1つの根があることが知られている区間を保存し、そうでなければ再び分割を繰り返すことです。これに関する問題は、根のクラスターが存在する場合に多くの分割が必要であることと、マッピングの計算で発生する数値的問題です。

Sagaraloff、Melhorn、Kobel、およびRouillierの作業は、可能な場合に区間のサイズを迅速に減少させるためのニュートンテストと境界テストを導入し、正確な算術の代わりに有限精度算術を使用してDescartesの上限を計算する能力を追加し、他のアルゴリズムの改善（すべてがここで実装されているわけではありません）を行います。

!!! note
    平方自由多項式は`p/gcd(p, p')`を通じて見つけることができますが、実際にはこの計算は数値的に不安定です。


!!! note
    この実装は、`Hecke.jl`の`arblib`を通じて提供される`Hecke.roots`関数よりも**はるかに**遅いです。これは、より専門的な実装（論文の著者によって提供されるものなど）と競争力がないと言われています（http://anewdsc.mpi-inf.mpg.de/）。いくつかの理由があります：`mobius_transform!`関数は`𝑶(n²)`であり、より多くの努力で`𝑶(n⋅log(n))`にすることができます。`admissiblepoint`での多項式評価も同様に効率的にすることができます。`BigFloat`型でのアロケーションを減らすために`MutableArithmetics.jl`パッケージから学んだトリックを使用しているにもかかわらず、精度が変更されるたびに新しい（アロケーションする）値を作成しなければならないため、アロケーションが*はるかに*多すぎます（`set_prec!`を使用するとセグメンテーションフォルトが発生します）。Kobel、Rouillier、およびSagraloffによって提案された重要なエンジニアリングのスピードアップは実装されていません。など。

など。

