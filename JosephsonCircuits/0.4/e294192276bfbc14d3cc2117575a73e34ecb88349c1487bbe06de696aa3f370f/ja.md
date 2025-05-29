```
connectS(Sa::AbstractArray, k::Int, l::Int;
    nbatches::Int = Base.Threads.nthreads())
```

ポート `k` と `l` を同じ `m` ポートマイクロ波ネットワークに接続し、散乱パラメータ行列 `Sa` で表される `(m-2)` ポートネットワークを生成します。以下に示すように：

入力ネットワーク:

```
      m |         | l+1    
        |   ...   |         l
        |_________|__________ 
        |         |          |
        |   Sa    |  ...     |
        |  m x m  |          |
    ____|_________|_____ k+1 |
    1   |   ...   |          |
        |         | k        |
      2 |         |__________|
```

出力ネットワーク:

```
    m-2 |         | l-1     
        |         |         
        |   ...   |         
        |_________|         
        |         |         
        |    S    |  ...    
        |m-2 x m-2|         
    ____|_________|_________
    1   |   ...         k   
        |                   
        |                   
      2 |                   
```

# 引数

  * `Sa::Array`: ポートが最初の2次元に沿って配置され、任意の数の他の次元（例：周波数）を持つネットワークを表す散乱パラメータの配列。
  * `k::Int`: 接続する最初のポート、1ベースのインデックス。
  * `l::Int`: 接続する2番目のポート、1ベースのインデックス。

# 参考文献

V. A. Monaco と P. Tiberio, "Computer-Aided Analysis of Microwave Circuits," in IEEE Transactions on Microwave Theory and Techniques, vol. 22, no. 3, pp. 249-263, Mar. 1974, doi: 10.1109/TMTT.1974.1128208.
