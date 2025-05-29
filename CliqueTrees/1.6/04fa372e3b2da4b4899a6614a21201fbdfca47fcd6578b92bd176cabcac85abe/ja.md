```
METIS <: EliminationAlgorithm

METIS(; ctype=-1, rtype=-1, nseps=-1, niter=-1, seed=-1,
        compress=-1, ccorder=-1, pfactor=-1, ufactor=-1)
```

METISで実装された多層[ネストされた分割](https://en.wikipedia.org/wiki/Nested_dissection)アルゴリズム。

```julia-repl
julia> using CliqueTrees, Metis

julia> graph = [
           0 1 0 0 0 0 0 0
           1 0 1 0 0 1 0 0
           0 1 0 1 0 1 1 1
           0 0 1 0 0 0 0 0
           0 0 0 0 0 1 1 0
           0 1 1 0 1 0 0 0
           0 0 1 0 1 0 0 1
           0 0 1 0 0 0 1 0
       ];

julia> alg = METIS(ctype=Metis.METIS_CTYPE_RM)
METIS:
    ctype: 0
    rtype: -1
    nseps: -1
    niter: -1
    seed: -1
    compress: -1
    ccorder: -1
    pfactor: -1
    ufactor: -1


julia> treewidth(graph; alg)
3
```

### パラメータ

  * `ctype`: 簡約中に使用されるマッチングスキーム
  * `rtype`: 精緻化に使用されるアルゴリズム
  * `nseps`: ネストされた分割の各レベルで計算される異なるセパレータの数
  * `niter`: 簡約解除プロセスの各段階での精緻化アルゴリズムの反復回数
  * `seed`: ランダムシード
  * `compress`: 同一の隣接リストを持つ頂点を結合するかどうか
  * `ccorder`: 接続成分を別々に順序付けるかどうか
  * `pfactor`: 最後に順序付けられる頂点の最小次数
  * `ufactor`: 許可される最大負荷不均衡パーティション

### 参考文献

  * Karypis, George, and Vipin Kumar. "不規則グラフの分割のための高速かつ高品質の多層スキーム。" *SIAM Journal on Scientific Computing* 20.1 (1998): 359-392.
