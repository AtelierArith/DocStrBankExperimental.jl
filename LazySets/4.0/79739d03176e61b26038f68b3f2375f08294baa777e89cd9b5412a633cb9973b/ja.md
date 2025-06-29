```
ρ(d::AbstractVector, cap::Intersection{N, S1, S2};
  algorithm::String="line_search", kwargs...
 ) where {N, S1<:LazySet,
             S2<:Union{HalfSpace, Hyperplane, Line2D}}
```

与えられた方向におけるコンパクト集合と半空間/ハイパープレーン/直線の交差の支持関数を評価します。

### 入力

  * `d`         – 方向
  * `cap`       – コンパクト集合と半空間/ハイパープレーン/直線の遅延交差
  * `algorithm` – （オプション、デフォルト: `"line_search"`）：支持関数を計算するためのアルゴリズム；有効なオプションは：

      * `"line_search"` – ブレント法または黄金分割法を使用して関連する単変数最適化問題を解決します
      * `"projection"`  – ハイパープレーン/直線との交差にのみ有効；与えられた方向 `d` とハイパープレーンの法線ベクトル `n` によって生成される平面における与えられたコンパクト集合のランク2線形変換の2D交差に問題を還元することによって支持関数を評価します
      * `"simple"`      – 各オペランドの支持関数評価の $\min$ を取ります

### 出力

与えられた方向における集合 `cap` の支持関数のスカラー値。

### 注意事項

交差の最初の集合（`cap.X`）がコンパクトであると仮定します。

アルゴリズムバックエンドへの追加の引数はキーワード引数として渡すことができます。

### アルゴリズム

アルゴリズムは関連する最適化問題を解くことに基づいています

$$
\min_{λ ∈ D_h} ρ(ℓ - λa, X) + λb.
$$

ここで、$D_h = \{ λ : λ ≥ 0 \}$ は $H$ が半空間の場合、または $D_h = \{ λ : λ ∈ ℝ \}$ は $H$ がハイパープレーンの場合です。

追加情報については [Frehse012, LeGuernic09, RockafellarW98](@citet) を参照してください。
