```julia
(1) 関数 testCV(cv1::CVresult, cv2::CVresult; 
               	direction = PermutationTests.Both())

(2) 関数 testCV(𝐞₁::Vector{BitVector}, 𝐞₂::Vector{BitVector}; 
               	direction = PermutationTests.Both())

```

(1) 二つの [`CVres`](@ref) 構造体 `cv1` と `cv2` を与えられた場合、これは [`crval`](@ref) メソッドを呼び出すことで取得でき、交差検証 `cv1` と `cv2` で得られた平均バイナリエラー損失の分布の違いに対してベイリスのテスト (Bayles et *al.*, 2020[🎓](@ref)) を実行します。これは、異なる機械学習モデルや、同じデータに対する異なる前処理、処理、または前条件付けパイプラインによって得られたパフォーマンスを比較するために使用できます。

!!! warning "注意"
    二つのモデルやパイプラインを交差検証で比較する際には、[`crval`](@ref) でキーワード引数 `shuffle=true` を使用しないでください。この場合、フォールドを構成する実際のデータは同一ではなくなります。また、`seed` キーワード引数を使用する場合は、二つの交差検証で同じシードが使用されていることを確認してください。


(2) この関数は、ここでのメソッド (2) で示されるように、エラー損失を直接引数として受け取ることもできます。この場合、𝐞₁ と 𝐞₂ は各フォールドで得られたエラー損失のベクトルを保持するベクトルです。フォーマットは、[`CVres`](@ref) 構造体にエラー損失を格納するために使用されるものと同じです。

$$
μ_1
$$

と $μ_2$ をそれぞれ `cv1` と `cv2` (または `𝐞₁` と `𝐞₂`) の平均損失とすると、`direction` キーワード引数はテストの方向性を決定します：

  * $$
    H_1: μ_1 > μ_2
    $$

    (use `direction=PermutationTests.Right()`)
  * $$
    H_1: μ_1 < μ_2
    $$

    (use `direction=PermutationTests.Left()`)
  * $$
    H_1: μ_1 <> μ_2
    $$

    (use `direction=PermutationTests.Both()`, the default)

すべての場合において $H_0: μ_1 = μ_2$ です。

!!! tip "精度に関するテストの方向"
    `direction=PermutationTests.Right()` でテストが有意である場合、`cv1` (または `𝐞₁`) のエラー損失は `cv2` (または `𝐞₂`) のエラー損失よりも統計的に優れていることに注意してください。これは、`cv1` (または `𝐞₁`) の精度が `cv2` (または `𝐞₂`) の精度よりも統計的に **劣っている** ことを意味します。


3-タプル (*z, p, ase*) を返し、$z$ テスト統計量 (標準偏差)、$p$-値、および漸近標準誤差を保持します。

!!! warning "クラスの不均衡"
    エラー損失は精度を反映しており、バランス精度ではありません。クラスが不均衡な場合、テストは多数派クラスによって駆動されます。[`crval`](@ref) に関するドキュメントも参照してください。


**例**:

```julia
using PosDefManifoldML

## 異なるデータに対する同じモデルとパイプラインのパフォーマンスをテスト:

# 同じ分布を持つ二つのランダムデータセットを生成
P1, _dummyP, y1, _dummyy = gen2ClassData(10, 60, 80, 30, 40, 0.01)
P2, _dummyP, y2, _dummyy = gen2ClassData(10, 60, 80, 30, 40, 0.01)

# 二つのデータセットに対して交差検証を実行
cv1 = crval(MDM(Fisher), P1, y1; scoring=:a)
cv2 = crval(MDM(Fisher), P2, y2; scoring=:a)

z, p, ase = testCV(cv1, cv2) # 両側テスト

# これは次のように等価です
z, p, ase = testCV(cv1.losses, cv2.losses)

## 同じデータに対する異なるメトリックのパフォーマンスをテスト:

# 同じ分布を持つ二つのランダムデータセットを生成
P, _dummyP, y, _dummyy = gen2ClassData(10, 40, 40, 30, 40, 0.15)

cv1 = crval(MDM(logEuclidean), P, y; scoring=:a)
cv2 = crval(MDM(Wasserstein), P, y; scoring=:a)

z, p, ase = testCV(cv1, cv2) # 両側テスト

```
