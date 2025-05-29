```
newickstring(njc::NJClust, tiplabels=AbstractVector{<:String}; labelinternalnodes=false)
newickstring(merges::AbstractArray{<:Integer}, heights::AbstractArray{<:AbstractFloat}, tiplabels::AbstractVector{<:String}; labelinternalnodes=false)
```

マージのリストをnewicktree形式の文字列に変換します。

# 引数:

  * njc: マージと高さを持つ構造体です
  * NJClust構造体からのマージと高さ:

      * マージはn-1 x 2の整数行列です: 負の整数の絶対値は距離行列へのインデックスを示します（すなわち、葉）。正の整数はマージリストへのインデックスを示します（すなわち、k番目の内部ノード）
      * 高さはn-1 x 2の行列で、各値は親からの左（1）または右（2）の子の距離です。具体的には`heights[i,j]`は`j`番目の子の親ノードへの距離で、行`i`です。
  * tiplabels: 距離行列の葉の順序に対応する文字列ラベルのベクトル
  * labelinternalnodes: 内部ノードのノードラベルを生成するかどうか。デフォルトは`false`です。

# 戻り値:

  * newicktree形式の文字列

# 例:

```jldoctest
julia> d = [
           0  5  9  9 8
           5  0 10 10 9
           9 10  0  8 7
           9 10  8  0 3
           8  9  7  3 0
       ];

julia> njclusts = regNJ(d)
NJClust{Int64, Float64}([-2 -1; -3 1; -4 2; -5 3], [3.0 2.0; 4.0 3.0; 2.0 2.0; 0.5 0.5])

julia> nwstring = newickstring(njclusts)
"(5:5.000000e-01,(4:2.000000e+00,(3:4.000000e+00,(2:3.000000e+00,1:2.000000e+00):3.000000e+00):2.000000e+00):5.000000e-01):0.000000e+00;"
```
