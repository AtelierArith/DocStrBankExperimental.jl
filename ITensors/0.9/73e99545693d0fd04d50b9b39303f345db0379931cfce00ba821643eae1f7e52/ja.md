```
svd(A::ITensor, inds::Index...; <keyword arguments>)
```

ITensor `A` の特異値分解 (SVD) を行い、提供された「左インデックス」を行インデックスとして、残りの「右インデックス」を列インデックスとして扱うことによって計算します（テンソルの行列化）。

最初の3つの戻り値は `U`、`S`、および `V` であり、`A ≈ U * S * V` となります。

SVD が切り捨てを行うかどうかは、提供されたキーワード引数によります。

左または右のインデックスのセットが空である場合、すべての入力インデックスはそれぞれ `V` または `U` に配置されます。左インデックスの空のセットを指定するには、明示的に `svd(A, ())` を使用する必要があります（`svd(A)` は現在未定義です）。

# 例

インデックス i と k が U に、j が V に配置されるように、3次の ITensor の SVD を計算します。

```
i = Index(2)
j = Index(5)
k = Index(2)
A = random_itensor(i, j, k)
U, S, V = svd(A, i, k);
@show norm(A - U * S * V) <= 10 * eps() * norm(A)
```

次のコードは、特異値の合計が4であるため、最後の2つの特異値を切り捨てます。元のテンソルとの違いのノルムは、切り捨てられた特異値の平方和の平方根になります。

```
trunc, Strunc, Vtrunc = svd(A, i, k; maxdim=2);
@show norm(A - Utrunc * Strunc * Vtrunc) ≈ sqrt(S[3, 3]^2 + S[4, 4]^2)
```

また、特異値の重みを特定のカットオフまで切り捨てることを指定することもできるため、合計誤差はカットオフを超えないようになります。

```
Utrunc2, Strunc2, Vtrunc2 = svd(A, i, k; cutoff=1e-10);
@show norm(A - Utrunc2 * Strunc2 * Vtrunc2) <= 1e-10
```

# キーワード

  * `maxdim::Int`: 保持する特異値の最大数。
  * `mindim::Int`: 保持する特異値の最小数。
  * `cutoff::Float64`: SVD の望ましい切り捨て誤差を設定します。デフォルトでは、最小の特異値の平方和として定義されます。
  * `lefttags::String = "Link,u"`: `U` と `S` で共有されるインデックスのタグを設定します。
  * `righttags::String = "Link,v"`: `S` と `V` で共有されるインデックスのタグを設定します。
  * `alg::String = "divide_and_conquer"`。オプション:
  * `"divide_and_conquer"` - 分割統治アルゴリズム。LAPACK の gesdd。高速ですが、非常に条件の悪い行列に対しては不正確な特異値をもたらす可能性があります。また、収束に失敗することもあり、その場合は「qr_iteration」または「recursive」を試すことができます。

      * `"qr_iteration"` - 通常は遅いですが、非常に条件の悪い行列に対しては `"divide_and_conquer"` よりも正確です。LAPACK の gesvd。
      * `"recursive"` - ITensor のカスタム SVD。非常に信頼性がありますが、高精度が必要な場合は遅くなる可能性があります。行列 `A` の `svd` を取得するために、$A^{\dagger} A$ の固有分解を使用して `U` を計算し、その後 $A^{\dagger} U$ の `qr` を使用して `V` を計算します。これは、小さな特異値を計算するために再帰的に実行されます。
  * `use_absolute_cutoff::Bool = false`: `cutoff` 値未満のすべての確率重みを破棄するかどうかを設定します。破棄された重みの合計ではなく。
  * `use_relative_cutoff::Bool = true`: 切り捨てのために特異値を正規化するかどうかを設定します。
  * `min_blockdim::Int = 0`: ブロックスパースまたは QN ITensor の SVD のために、可能な限り保持される特異値の数がこの値以上であることを要求します。

参照: [`factorize`](@ref), [`eigen`](@ref)
