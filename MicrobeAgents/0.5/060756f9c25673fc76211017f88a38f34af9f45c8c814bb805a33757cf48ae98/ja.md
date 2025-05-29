```
StandardABM(MicrobeType, space, timestep; kwargs...)
```

微生物タイプのための `Agents.StandardABM` メソッドの拡張。エージェントをいつでも追加および削除できる `AgentBasedModel` の実装。エージェントの削除が必要ない場合は、パフォーマンス向上のためにキーワード引数 `container = Vector` を使用することをお勧めします。キーワード引数の詳細については `Agents.AgentBasedModel` を参照してください。

**引数**

  * `MicrobeType`: 明示的に指定された次元 `D` を持つ `AbstractMicrobe{D}` のサブタイプ。利用可能なオプションのリストは `subtypes(AbstractMicrobe)` を実行することで取得できます。
  * `space`: 微生物タイプと同じ次元 `D` を持つ `ContinuousSpace{D}` で、シミュレーション領域の空間的特性を指定します。
  * `timestep`: シミュレーションの統合タイムステップ。

**キーワード**

  * `properties`: モデルレベルのプロパティを指定するための追加データコンテナ。MicrobeAgents.jl にはデフォルトのプロパティのセットが含まれています（詳細は最後に記載）。
  * `scheduler = Schedulers.fastest`
  * `rng = Random.default_rng()`
  * `warn = true`

**デフォルトの `properties`**

モデルが作成されると、デフォルトのプロパティのセットがモデルに含まれます (`MicrobeAgents.default_ABM_properties`):

```
DEFAULT_ABM_PROPERTIES = Dict(
    :chemoattractant => GenericChemoattractant{D,Float64}()
    :affect! => chemotaxis!
)
```

これらのデフォルトプロパティを含めることで、追加のユーザー介入なしでもすべてのケモタクシスモデルが機能することを保証します。これらのプロパティは、モデルを作成する際に `properties` 辞書に同等のキーを渡すことで上書きできます。
