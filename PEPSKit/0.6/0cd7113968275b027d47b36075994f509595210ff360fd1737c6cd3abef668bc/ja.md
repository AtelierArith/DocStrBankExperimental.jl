```
leading_boundary(env₀, network; kwargs...) -> env, info
# expert version:
leading_boundary(env₀, network, alg::CTMRGAlgorithm)
```

CTMRGを使用して`network`を収縮し、CTM環境を返します。アルゴリズムはキーワード引数を介して、または直接[`CTMRGAlgorithm`](@ref)構造体として供給できます。

## キーワード引数

### CTMRG反復

  * `tol::Real=1.0e-8` : CTMRG反復の停止基準。これはノルム収束と、コーナーおよびエッジの特異値の距離です。
  * `miniter::Int=4` : CTMRG反復の最小回数。
  * `maxiter::Int=100` : CTMRG反復の最大回数。
  * `verbosity::Int=2` : 出力の冗長性レベルで、次のいずれかである必要があります：

    0. すべての出力を抑制
    1. 警告のみを表示
    2. 初期化および収束情報
    3. 反復情報
    4. デバッグ情報
  * `alg::Symbol=:simultaneous` : CTMRGアルゴリズムのバリアント。詳細は[`CTMRGAlgorithm`](@ref)を参照してください。

      * `:simultaneous`: すべての側面の同時展開と再正規化。
      * `:sequential`: 左の移動と回転の順次適用。

### プロジェクターアルゴリズム

  * `trscheme::Union{TruncationScheme,NamedTuple}=(; alg::Symbol=:fixedspace)` : プロジェクター計算のための切り捨てスキームで、結果として得られる仮想空間を制御します。ここで、`alg`は次のいずれかであることができます：

      * `:fixedspace` : 投影中に仮想空間を固定
      * `:notrunc` : 特異値は切り捨てられず、実行されるSVDは正確
      * `:truncerr` : 追加の誤差閾値`η`を供給；最大仮想次元`η`に切り捨て
      * `:truncdim` : 追加の切り捨て次元`η`を供給；切り捨てられた値の2ノルムが`η`より小さくなるように切り捨て
      * `:truncspace` : 追加の切り捨て空間`η`を供給；供給されたベクトル空間に従って切り捨て
      * `:truncbelow` : 追加の特異値カットオフ`η`を供給；保持される特異値がすべて`η`より大きくなるように切り捨て
  * `svd_alg::Union{<:SVDAdjoint,NamedTuple}` : プロジェクターを計算するためのSVDアルゴリズム。詳細は[`SVDAdjoint`](@ref)を参照してください。デフォルトでは、`krylovdim`が`env₀`環境の次元に適応される逆ルールの許容誤差`tol=1e1tol`です。
  * `projector_alg::Symbol=:halfinfinite` : プロジェクターアルゴリズムのバリアント。詳細は[`ProjectorAlgorithm`](@ref)を参照してください。

      * `:halfinfinite` : 半無限（2つの拡張コーナー）のCTMRG環境のSVDによる投影。
      * `:fullinfinite` : 完全無限（すべて4つの拡張コーナー）のCTMRG環境のSVDによる投影。

## 戻り値

CTMRGルーチンは、最終的なCTMRG環境と、次のフィールドを含む情報`NamedTuple`を返します：

  * `truncation_error` : CTMRGプロジェクターの最後の（最大の）SVD切り捨て誤差。
  * `condition_number` : 拡張されたCTMRG環境の最後の（最大の）条件数。

`alg`が`SimultaneousCTMRG`の場合、最後のSVDも返されます：

  * `U` : 左特異ベクトルの最後の単位セル。
  * `S` : 特異値の最後の単位セル。
  * `V` : 右特異ベクトルの最後の単位セル。

さらに、指定されたSVDアルゴリズムが完全で切り捨てられていないSVDを計算する場合、すべてのベクトルと値の完全なセットも返されます：

  * `U_full` : すべての左特異ベクトルの最後の単位セル。
  * `S_full` : すべての特異値の最後の単位セル。
  * `V_full` : すべての右特異ベクトルの最後の単位セル。

```
