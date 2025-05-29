```
process(self::HMM, d::Array{T, 2}, splitSw::Bool;
params::HMMParams) where T <: Number
```

# 説明

隠れマルコフモデルオブジェクトを処理します。反復的な変更関数として意図されており、いくつかのステップを実行します：

  * モデルのトレースバックをリセットします。
  * フレームをモデルデータに供給します。
  * モデルを更新します。
  * 仮定された新しい状態を生成します。

参照： [`setup`](@ref), [`HMM`](@ref), [`HMMParams`](@ref)
