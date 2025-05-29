```julia
function table2vec(table::Matrix{I}, stat::IndSampStatistic) 

function table2vec(tables::AbstractVector{Matrix{I}}, stat::IndSampStatistic) 

function table2vec(table::Matrix{I}, stat::RepMeasStatistic) 

function table2vec(tables::AbstractVector{Matrix{I}}, stat::RepMeasStatistic) 

    where I<:Int

```

二項データのテーブルをフォーマットして、テスト関数のデータ入力を作成します。

フォーマットされたテーブルをベクトル（単変量テスト用）またはベクトルのベクトル（多重比較テスト用）として保持する2タプルと、適切な引数 [ns](@ref) を返します。

これらの関数は一般的には使用する必要はありません。テスト関数によって内部的に呼び出されます。ただし、二項データのために [独自のテストを作成する](@ref "Create your own test") 場合には便利です。

`stat` は [Statistic](@ref) 型のシングルトンであり、すなわち [テスト統計量のグループ](@ref "Statistic groups") のいずれかに属するテスト統計量です。

これらの関数の使用については、それらを使用するテスト関数のドキュメントを参照してください：

**単変量テスト関数**

  * [`chiSquaredTest`](@ref)
  * [`fisherExactTest`](@ref)
  * [`cochranqTest`](@ref)
  * [`mcNemarTest`](@ref)

**多重比較テスト関数**

  * [`chiSquaredMcTest`](@ref)
  * [`fisherExactMcTest`](@ref)
  * [`cochranqMcTest`](@ref)
  * [`mcNemarMcTest`](@ref)
