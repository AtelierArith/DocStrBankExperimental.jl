タイプ: OneDAtX

メソッド: update!, reinit!, copy

イテレーション間のラインサーチ情報を追跡するために設計された構造体。f : ℜⁿ → ℜを与えられたとき、h(θ) = f(x + θ*d)と定義します。ここで、xとdは同じ次元のベクトルで、θはスカラー、より具体的にはステップサイズです。

追跡されるデータには以下が含まれます：

  * x             : 現在のステップサイズ
  * fx [opt]      : 現在のイテレーションにおけるh(θ)
  * gx [opt]      : h'(θ)
  * f₀ [opt]      : h(0)
  * g₀ [opt]      : h'(0)
  * d [opt]       : 探索方向
  * res [opt]     : 残差
  * current_time  : ラインサーチアルゴリズムが開始された時刻。
  * current_score : ラインサーチアルゴリズムが開始されたスコア。

コンストラクタ:  `OneDAtX(:: T, :: S; fx :: T = _init_field(T), gx :: T = _init_field(T), f₀ :: T = _init_field(T), g₀ :: T = _init_field(T), current_time :: Float64 = NaN) where {S, T <: Number}`

`OneDAtX(:: T; fx :: T = _init_field(T), gx :: T = _init_field(T), f₀ :: T = _init_field(T), g₀ :: T = _init_field(T), current_time :: Float64 = NaN, current_score :: T = _init_field(T))  where T <: Number`

注意:

  * デフォルトでは、未知のエントリは`_init_field`を使用して設定されます。
  * デフォルトで`current_score`の型は`eltype(x)`であり、Stateが作成されると変更できません。長さnのベクトル化された`current_score`を持つには、`OneDAtX(x, Array{eltype(x),1}(undef, n))`を使用してください。
