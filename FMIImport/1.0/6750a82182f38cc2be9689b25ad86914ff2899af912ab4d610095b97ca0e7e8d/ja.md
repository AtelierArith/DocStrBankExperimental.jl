```
fmi3SetContinuousStates(c::FMU3Instance, x::Union{AbstractArray{Float32}, AbstractArray{Float64}})
```

新しい（連続）状態ベクトルを設定し、状態に依存する変数のキャッシュを再初期化します。引数 nx はベクトル x の長さであり、チェックの目的で提供されます。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 2.0.2 標準の FMU のインスタンス化されたインスタンスを表します。
  * `x::Union{AbstractArray{Float32},AbstractArray{Float64}}`: 引数 `x` は `Float64` または `Float32` のベクトル値の `AbstractArray` です。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 3.2.1. 状態: 連続時間モード

さらに [`fmi3SetContinuousStates`](@ref) を参照してください。
