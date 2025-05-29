```julia

# METHOD 1
function testStatistic(x, y, stat::mystat, fstat::Function; 
                        cpcd=nothing, kwargs...)

# METHOD 2
function testStatistic(x, Y, i::Int, stat::mystat, fstat::Function; 
                        cpcd=nothing, kwargs...)
                        
        where mystat<:Statistic 
```

単変量テストの観測されたおよび置換された検定統計量を計算します（方法1）または、$i^{th}$ 仮説の観測されたおよび置換された検定統計量を計算します。$i=1...M$ の多重比較置換テスト（方法2）に対して。

もしあなたが [create your own test](@ref "Create your own test") を作成するなら、宣言した [Statistic](@ref) 型の検定統計量を `stat` としてこれらの関数の新しいメソッドを書くことになります。

そうでなければ、これらの関数は必要ありません。

`Y` は要素のベクトル（通常はベクトル自体）であり、検定統計量は `Y[i]` に対して計算され、置換ベクトル `x` を使用します。

`fstat` および `cpcd` 引数については、[create your own test](@ref "Create your own test") を参照してください。
