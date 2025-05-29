```
paramscan(parameters::AbstractDict, initialize; kwargs...) → adf, mdf
```

ABMシミュレーションの出力のパラメータスキャンを実行し、すべてのパラメータの組み合わせからデータを収集してデータフレーム（エージェントデータ用とモデルデータ用の1つずつ）に格納します。データフレームの列は、収集されたデータ（[`run!`](@ref)のように）と、使用された入力パラメータの値の両方です。

`parameters`は、キーの型が`Symbol`の辞書です。辞書の各エントリは、スキャンするべきパラメータキーをパラメータ値にマッピングします（または、スキャン中に一定のままの単一のパラメータ値にマッピングします）。`parameters`に関するアプローチは次のとおりです。

  * 特定のキーの値が`Vector`である場合、そのベクターのすべての値がスキャンするパラメータの値として展開されます。
  * 特定のキーの値が`Vector`でない場合、その値は単一で一定のパラメータ値に対応すると見なされ、したがって展開またはスキャンされません。

これは、`String`のように本質的に反復可能なパラメータ値がその構成要素に誤って展開されないようにするために行われます（パラメータの値自体が`Vector`である場合、スキャンするためにはベクターのベクターを渡す必要があります）。

2番目の引数`initialize`は、ABMを作成して返す関数です。これは、`parameters`辞書の*キー*であるキーワード引数を受け入れる必要があります。ユーザーが入力引数を使用してABMを作成する方法を決定するため、`parameters`はモデルのプロパティ、スペースのタイプと作成、エージェントのプロパティに影響を与えるために使用できます。以下の例を参照してください。

## キーワード

次のキーワードは`paramscan`関数を修正します：

  * `include_constants::Bool = false`: デフォルトでは、出力`DataFrame`には変動するパラメータ（`parameters`内の`Vector`値）のみが含まれます。`true`の場合、定数パラメータ（`parameters`内の非Vector）も含まれます。
  * `parallel::Bool = false`: シミュレーションを並行して実行するために`Distributed.pmap`が呼び出されるかどうか。これは`@everywhere`と併用する必要があります（[パフォーマンステクニック](@ref)を参照）。
  * `showprogress::Bool = false`: 完了した%の実行を示すプログレスバーが表示されるかどうか。

他のすべてのキーワードは[`run!`](@ref)に伝播されます。さらに、`n`もここでキーワードとして、[`run!`](@ref)に引数として渡されます。もちろん、時間ステップの数`n`と少なくとも1つの`adata, mdata`は必須です。`adata, mdata`リストには、重複を避けるために`parameters`辞書にすでに含まれているパラメータを含めるべきではありません。

## 例

`paramscan`を使用した実行可能な例は、[シェリングの分離モデル](@ref Tutorial)に示されています。そこで、次のように定義します。

```julia
function initialize(; numagents = 320, griddims = (20, 20), min_to_be_happy = 3)
    space = GridSpaceSingle(griddims, periodic = false)
    properties = Dict(:min_to_be_happy => min_to_be_happy)
    model = StandardABM(SchellingAgent, space;
                properties = properties, scheduler = Schedulers.randomly)
    for n in 1:numagents
        add_agent_single!(SchellingAgent, model, n < numagents / 2 ? 1 : 2)
    end
    return model
end
```

そして、次のようにパラメータスキャンを実行します。

```julia
happyperc(moods) = count(moods) / length(moods)
adata = [(:mood, happyperc)]

parameters = Dict(
    :min_to_be_happy => collect(2:5), # 展開される
    :numagents => [200, 300],         # 展開される
    :griddims => (20, 20),            # 非Vector = 展開されない
)

adf, _ = paramscan(parameters, initialize; adata, n = 3)
```
