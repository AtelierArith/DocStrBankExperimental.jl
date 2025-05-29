```
AugStateParams(N::Int, mu::AbstractVector{T}, Phi::AbstractMatrix{T}, 
               Sigma::AbstractMatrix{T}, B::AbstractMatrix{T}, 
               C::Vector{<:AbstractMatrix{T}}) where {T<:Real}
```

拡張ダイナミクスをカプセル化する拡張状態パラメータオブジェクトを構築します。この関数は、フィルタリングおよびスムージング中に測定方程式の二次成分が適切に処理されるように、従来の状態空間パラメータに基づいて追加の構造と行列を計算します。

# 引数

  * N::Int: 状態ベクトルの次元。
  * mu::AbstractVector{T}: 初期状態平均ベクトル。
  * Phi::AbstractMatrix{T}: 状態遷移行列。
  * Sigma::AbstractMatrix{T}: 状態イノベーションの共分散行列。
  * B::AbstractMatrix{T}: 測定設計行列。
  * C::Vector{<:AbstractMatrix{T}}: 各測定要素の二次係数行列のベクトル。各要素は、測定方程式への二次寄与を表すN×N行列でなければなりません。

# 戻り値

次のフィールドを持つAugStateParamsのインスタンス:

  * mu_aug: muとSigmaから計算された拡張状態平均ベクトル。
  * Phi_aug: muとPhiから導出された拡張状態遷移行列。
  * B_aug: BとCの行列のセットから計算された拡張測定行列。
  * H_aug: 状態空間表現を変換する際に使用される拡張選択行列。
  * G_aug: 二次形式の対称性を処理するために使用される拡張重複行列。
  * Lambda: 二次項の構造的特徴を捉えるために計算された行列。
  * L1, L2, L3: モーメント計算をサポートするためにSigmaとLambdaから導出された補助行列。
  * P: N + N^2で与えられる総拡張状態次元を示す整数。

# 詳細

この関数は次のステップを実行します:

1. 二次測定定式の重要な側面をカプセル化するヘルパー関数を介してLambdaを計算します。
2. 元の平均と共分散Sigmaを使用して拡張状態平均(mu_aug)を計算します。
3. 拡張ダイナミクスに従ってPhiを変換することにより、拡張状態遷移行列(Phi_aug)を計算します。
4. 元のBと二次係数行列Cを組み合わせることにより、拡張測定行列(B_aug)を決定します。
5. 次のモーメントおよび分散計算に必要な補助行列L1、L2、およびL3を計算します。
6. ヘルパー関数を使用して選択行列(H)と重複行列(G)を生成し、拡張コンテキストに適合させるためにH*augおよびG*augにさらに洗練します。
7. 元の状態次元とその平方の合計として、全体の拡張状態次元Pを設定します。

この関数を呼び出す前に、すべてのヘルパー関数（例: compute*Lambda, compute*mu*aug, compute*Phi*aug, compute*B*aug, compute*L1, compute*L2, compute*L3, selection*matrix, duplication*matrix, compute*H*aug, および compute*G*aug）が定義され、スコープ内にあることを確認してください。
