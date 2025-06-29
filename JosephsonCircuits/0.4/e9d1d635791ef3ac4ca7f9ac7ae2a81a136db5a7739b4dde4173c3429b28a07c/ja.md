```
connectS(Sa::AbstractArray,Sb::AbstractArray,k::Int,l::Int;
    nbatches::Int = Base.Threads.nthreads())
```

ポート `k` を `m` ポートネットワーク（散乱パラメータ行列 `Sa` で表される）に接続し、ポート `l` を `n` ポートネットワーク（散乱パラメータ行列 `Sb` で表される）に接続し、結果として単一の `(m+n-2)` ポートネットワークを生成します。以下に示すように：

入力ネットワーク：

```
      m |        | k+1                       | 2
        |        |                           |
        |   ...  |                     ...   |
        |________|                  _________|________
        |        |                  |        |       1
        |   Sa   |                  |   Sb   |
        |  m x m |                  |  n x n |
    ____|________|__________________|________|
    1   |   ...     k           l   |   ...  |
        |                           |        |
        |                           |        |
      2 |                       l+1 |        | n
```

出力ネットワーク：

```
    m-1 |        | k      | m+1    
        |        |        |        
        |   ...  |   ...  |        
        |________|________|________
        |                 |     m  
        |        S        |        
        |  m+n-2 x m+n-2  |        
    ____|_________________|        
    1   |   ...  |   ...  |        
        |        |        |        
        |        |        |        
      2 |        |        |  m+n-2 
                m-1+l              
```

# 引数

  * `Sa::Array`: 最初のネットワークを表す散乱パラメータの配列で、最初の2次元にポートがあり、その後に任意の数の他の次元（例：周波数）が続きます。
  * `Sb::Array`: 2番目のネットワークを表す散乱パラメータの配列で、最初の2次元にポートがあり、その後に任意の数の他の次元（例：周波数）が続きます。
  * `k::Int`: 最初のネットワークのポートで、1ベースのインデックスです。
  * `l::Int`: 2番目のネットワークのポートで、1ベースのインデックスです。

# 参考文献

V. A. Monaco and P. Tiberio, "Computer-Aided Analysis of Microwave Circuits," in IEEE Transactions on Microwave Theory and Techniques, vol. 22, no. 3, pp. 249-263, Mar. 1974, doi: 10.1109/TMTT.1974.1128208.
