```
solveQP(dmat::AbstractMatrix{T}, dvec::AbstractArray{T}, Amat::AbstractMatrix{T}, bvec::AbstractArray{T}; meq::Int = 0, factorized::Bool = false)::Tuple{AbstractArray{T},AbstractArray{T},T,AbstractArray{Int},Int,AbstractArray{Int}}
```

このルーチンは、二次計画問題を解くためのGoldfarbとIdnani（1982、1983）の双対法を実装しています。問題の形式は次のとおりです。

```
     minimize  -d^T x + 1/2 *  x^T D x
     where   A1^T x  = b1
             A2^T x >= b2
```

行列Dは正定値であると仮定されています。特に、Dは対称であると仮定されています。

# 入力パラメータ：

  * `dmat`   nxn行列、上記の行列D（通常はFloat64）      ユーザーには2つの選択肢があります：      a) Dを与える（factorized = false）、この場合、Dを分解するためにLINPACKのルーチンを使用します。      b) アルゴリズムを開始するために、R^-1が必要です。D=R^TRであるため、他の方法でR^-1を計算する方が安価である場合（Dはバンド行列である可能性があります）、ユーザーはR^{-1}を渡すことができます。これはfactorized = trueで示されます。
  * `dvec`   nx1ベクトル、上記のベクトルd（通常はFloat64）      出力時に初期の、すなわち制約のない問題の解を含みます。
  * `Amat`   nxq行列、上記の行列A（通常はFloat64） [ A=(A1 A2)^T ]、コピーされ、したがって変更されていません。
  * `bvec`   qx1ベクトル、制約の定数bのベクトル（通常はFloat64）      [ b = (b1^T b2^T)^T ]、コピーされ、したがって変更されていません。
  * `meq::Int=0`  等式制約の数、0 <= meq <= q。

# 出力パラメータは次の要素からなるタプルです：

1. sol   nx1 最終解（上記のx）
2. lagr  qx1 最終ラグランジュ乗数
3. crval スカラー、最小値での基準の値
4. iact  qx1ベクトル、最終的なフィットでアクティブな制約（int）
5. nact  スカラー、最終的なフィットでアクティブな制約の数（int）
6. iter  2x1ベクトル、最初の要素は「メイン」イテレーションの数を示し、2番目の要素はアクティブになった後に削除された制約の数を示します

```
