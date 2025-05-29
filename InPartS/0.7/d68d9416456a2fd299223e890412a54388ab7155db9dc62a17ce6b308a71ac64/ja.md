```
LineageCoordRegistrar{N, T<:Integer} <: AbstractSeqRegistrar{T}
```

コンストラクタ:

```
LineageCoordRegistrar{N, T = UInt64}()
LineageCoordRegistrar(next_id::T = UInt64(1); ndims::Integer, kwargs...)
```

この[`AbstractSeqRegistrar`](@ref)の実装は、型`T`（デフォルトは`UInt64`）の連続番号を返すだけでなく、`parent`という辞書を使用して系統を追跡し、粒子が追加された時刻と位置を記録することもできます。粒子は`SVector{N, Float64}`型の`centerpos`プロパティを持つと仮定されています。`ndims`は`N`を指定する別の方法です。最後の2つのコンストラクタは、キーワード引数を介して`parent`、`centerpos`、および`times`プロパティを事前に設定することも可能です。

このレジストラで[`set_id!`](@ref)/[`get_id!`](@ref)を呼び出すと、上記のデータが自動的に記録されます。

例:

```
# 二次元シミュレーションのためのデフォルト初期化されたレジストラ
reg = LineageCoordRegistrar(ndims=2)

# 同じだが型パラメータ付き
reg = LineageCoordRegistrar{2}()
```
