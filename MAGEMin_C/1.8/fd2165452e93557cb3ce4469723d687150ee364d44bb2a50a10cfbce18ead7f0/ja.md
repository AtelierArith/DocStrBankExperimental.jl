Out*PT =multi*point*minimization(P::T2,T::T2,MAGEMin*db::MAGEMin*Data;test::Int64=0,X::Union{Nothing, AbstractVector{Float64}, AbstractVector{<:AbstractVector{Float64}}}=nothing,B::Union{Nothing, T1, Vector{T1}}=nothing,W::Union{Nothing, Vector{MAGEMin*C.W*data{Float64, Int64}}}=nothing,Xoxides=Vector{String},sys*in="mol",progressbar=true,                                  callback*fn ::Union{Nothing, Function}= nothing,                                   callback*int::Int64 = 1) where {T1 <: Float64, T2 <: AbstractVector{T1}}

圧力 `P`、温度 `T`、および/または組成 `X` の関数として、複数の点に対して (並列) MAGEMin 計算を実行します。データベース `MAGEMin_db` は、ルーチンを呼び出す前に初期化されている必要があります。バルク岩の組成は、事前定義されたビルトインテストケースのいずれかに設定することも、`X`、`Xoxides`、および `sys_in` を渡すことによって特定に指定することもできます（これは、入力が "mol" または "wt" のいずれかであるかを指定します）。

以下はいくつかの例です：

# 例 1 - ビルトインテスト vs. 圧力と温度

```julia
julia> data = Initialize_MAGEMin("ig", verbose=false);
julia> n = 10
julia> P = rand(8:40.0,n)
julia> T = rand(800:1500.0,n)
julia> out = multi_point_minimization(P, T, data, test=0)
julia> Finalize_MAGEMin(data)
```

# 例 2 - すべての点に対して一定のバルク岩組成を指定：

```julia
julia> data = Initialize_MAGEMin("ig", verbose=false);
julia> n = 10
julia> P = fill(10.0,n)
julia> T = fill(1100.0,n)
julia> Xoxides = ["SiO2"; "Al2O3"; "CaO"; "MgO"; "FeO"; "Fe2O3"; "K2O"; "Na2O"; "TiO2"; "Cr2O3"; "H2O"];
julia> X = [48.43; 15.19; 11.57; 10.13; 6.65; 1.64; 0.59; 1.87; 0.68; 0.0; 3.0];
julia> sys_in = "wt"
julia> out = multi_point_minimization(P, T, data, X=X, Xoxides=Xoxides, sys_in=sys_in)
julia> Finalize_MAGEMin(data)
```

# 例 3 - 異なる点に対して異なるバルク岩組成

```julia
julia> data = Initialize_MAGEMin("ig", verbose=false);
julia> P = [10.0, 20.0]
julia> T = [1100.0, 1200]
julia> Xoxides = ["SiO2"; "Al2O3"; "CaO"; "MgO"; "FeO"; "Fe2O3"; "K2O"; "Na2O"; "TiO2"; "Cr2O3"; "H2O"];
julia> X1 = [48.43; 15.19; 11.57; 10.13; 6.65; 1.64; 0.59; 1.87; 0.68; 0.0; 3.0];
julia> X2 = [49.43; 14.19; 11.57; 10.13; 6.65; 1.64; 0.59; 1.87; 0.68; 0.0; 3.0];
julia> X = [X1,X2]
julia> sys_in = "wt"
julia> out = multi_point_minimization(P, T, data, X=X, Xoxides=Xoxides, sys_in=sys_in)
julia> Finalize_MAGEMin(data)
```

# julia でのマルチスレッドの有効化

マルチスレッドを活用するには、ターミナルから次のように julia を起動する必要があります：

```bash
$ julia -t auto
```

これにより、あなたのマシンのすべてのスレッドが自動的に使用されます。あるいは、`julia -t 4` を使用して 4 スレッドで起動します。あなたのマシンでできることを確認したい場合は、次のように入力してください：

```
julia> versioninfo()
```
