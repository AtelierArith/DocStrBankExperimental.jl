この関数は、最初の引数としてファイル名を、2番目の引数として`PairwiseListMatrix`を取ります。`diagonal`キーワード引数が`true`（デフォルト）である場合、対角線が出力に含まれます。キーワード引数`delim`（デフォルトは`'	'`）は、区切り文字として使用される文字を変更することを可能にします。

```jldoctest
julia> using PairwiseListMatrices, DelimitedFiles

julia> plm  = PairwiseListMatrix(trues(3), false)
3×3 PairwiseListMatrix{Bool,false,BitArray{1}}:
 false   true   true
  true  false   true
  true   true  false

julia> writedlm("example.csv", plm, diagonal=false, delim=',')

julia> println(read("example.csv", String))
1,2,true
1,3,true
2,3,true

```
