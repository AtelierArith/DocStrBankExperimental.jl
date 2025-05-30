```
solveQPcompact!(dmat::AbstractMatrix{T}, dvec::AbstractArray{T}, Amat::AbstractMatrix{T}, Aind::AbstractMatrix{Int}, bvec::AbstractArray{T}; meq::Int = 0, factorized::Bool = false)::Tuple{AbstractArray{T},AbstractArray{T},T,AbstractArray{Int},Int,AbstractArray{Int}}
```

このルーチンは、Goldfarb/Idnaniアルゴリズムを使用して、次の最小化問題を解決します：

```
    minimize  -d^T x + 1/2 *  x^T D x
    where   A1^T x  = b1
            A2^T x >= b2
```

行列Dは正定値であると仮定されています。特に、Dは対称であると仮定されています。

# 入力パラメータ

  * `dmat`   nxn行列、上記の行列D（dp）      ユーザーには2つの選択肢があります：      a) Dを与える（factorized=false）、この場合、Dを分解するためにLINPACKのルーチンを使用します。      b) アルゴリズムを開始するために、R^-1が必要です。ここでD=R^TRです。         したがって、一般的なルーチンで計算するよりも、別の方法でR^-1を計算する方が安価である場合（Dはバンド行列である可能性があります）、ユーザーはR^{-1}を渡すことができます。 これはfactorized = trueで示されます。
  * `dvec`   nx1ベクトル、上記のベクトルd（通常はFloat64）      出力時に初期の、すなわち制約のない問題の解を含みます。
  * `Amat`   lxq行列（通常はFloat64）。       等式制約に対応するエントリは、出力時に符号が変わる可能性があります。
  * `Aind`  (l+1)xq行列（Int）      これらの2つの行列は、コンパクト形式で行列Aを格納します。フォーマットは：[ A=(A1 A2)^T ]        Aind(1,i)は、Aの列iの非ゼロ要素の数です。        Aind(k,i)はk>=2の場合、Aの列iの(k-1)番目の非ゼロ要素がA(i,j)である場合、jに等しいです。        Aind(k,i)はk>=1の場合、Aの列iのk番目の非ゼロ要素に等しいです。
  * `bvec`   qx1ベクトル、制約の定数bのベクトル（通常はFloat64）      [ b = (b1^T b2^T)^T ]       等式制約に対応するエントリは、出力時に符号が変わる可能性があります。
  * `meq::Int=0`   等式制約の数、0 <= meq <= q。

# 出力パラメータ（タプルとして）

1. sol   nx1 最終的な解（上記の記法でのx）
2. lagr  qx1 最終的なラグランジュ乗数
3. crval スカラー、最小値での基準の値
4. iact  qx1ベクトル、最終的なフィットでアクティブな制約（int）
5. nact  スカラー、最終的なフィットでアクティブな制約の数（int）
6. iter  2x1ベクトル、最初のコンポーネントは「メイン」イテレーションの数を示し、2番目のコンポーネントはアクティブになった後に削除された制約の数を示します。

```
# ヒント
```

AmatとAindは、Aが標準のJuliaスパース行列である場合、convertSparse(A)関数を通じてJuliaスパース行列から作成できます。 ```
