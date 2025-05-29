```julia
abstract type AbstractLoopEvent <: Ignite.AbstractFiringEvent
```

通常の[`Ignite.run!`](@ref)の実行中に発生するイベントのための抽象スーパタイプです。

デフォルトの便利なコンストラクタ`(EVENT::Type{<:AbstractLoopEvent})(; kwargs...)`が提供されており、`AbstractLoopEvent`の簡単なフィルタリングを可能にします。例えば、`EPOCH_COMPLETED(every = 3)`は、3エポックごとにトリガーされる[`FilteredEvent`](@ref)を構築します。許可されているキーワードについては[`filter_event`](@ref)を参照してください。

`AbstractLoopEvent`から継承することで、カスタムイベントもこれらの便利なコンストラクタを継承します。これが望ましくない場合は、代わりにスーパタイプ`AbstractFiringEvent`から継承することができます。
