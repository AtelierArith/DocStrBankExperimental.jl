```
make_function(
    func_array::AbstractArray{<:Node},
    input_variables::AbstractVector{<:Node}...;
    in_place::Bool=false, init_with_zeros::Bool=true
)
```

`func_array`内の象徴的な式を評価するための関数を作成します。`func_array`で使用されるすべての変数は、`input_variables`にも含まれている必要があります。ただし、`input_variables`内の変数が`func_array`で使用されていない場合でもエラーは発生しません。

```julia
julia> @variables x
x

julia> f = x+1
(x + 1)


julia> jac = jacobian([f],[x]) #ヤコビ行列は単一の定数要素1を持ち、もはやxの関数ではありません
1×1 Matrix{FastDifferentiation.Node}:
 1

 julia> fjac = make_function(jac,[x])
 ...
 
 julia> fjac(2.0) #値2.0が変数xに渡されますが、出力には影響しません。ランタイム例外は発生しません。
 1×1 Matrix{Float64}:
  1.0
```

`in_place=false`の場合、関数が呼び出されるたびに結果を保持する新しい配列が作成されます。`in_place=true`の場合、関数は結果を保持するためにユーザーが提供した配列を期待します。ユーザーが提供した配列は、関数への最初の引数である必要があります。

```julia
julia> @variables x
x

julia> f! = make_function([x,x^2],[x],in_place=true)
...

julia> result = zeros(2)
2-element Vector{Float64}:
 0.0
 0.0

julia> f!(result,[2.0])
4.0

julia> result
2-element Vector{Float64}:
 2.0
 4.0
```

配列がスパースの場合、キーワード引数`init_with_zeros`は効果がありません。配列がデンスで`in_place=true`の場合、キーワード引数`init_with_zeros`はインプレース配列の初期化方法に影響します。`init_with_zeros = true`の場合、インプレース配列はゼロで初期化されます。`init_with_zeros=false`の場合、ユーザーはランタイム生成関数に渡す前に配列をゼロで初期化する責任があります。

これは、配列のエントリの少なくとも1/4が非ゼロであるような、適度にスパースなデンス行列に役立ちます。この場合、スパース行列はデンス行列ほど効率的ではないかもしれません。しかし、大部分の時間が不必要に要素をゼロに設定することに費やされる可能性があります。この場合、ランタイム生成関数を呼び出す前に、インプレースヤコビ行列配列を一度ゼロで初期化することができます。
