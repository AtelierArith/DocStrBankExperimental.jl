```
MultiScaleModel(model, mapped_variables)
```

モデルをマルチスケールにするための構造体です。モデルの変数と、値が取得されるノードシンボルとの間のマッピングを定義します。

# 引数

  * `model<:AbstractModel`: マルチスケールにするモデル
  * `mapped_variables<:Vector{Pair{Symbol,Union{AbstractString,Vector{AbstractString}}}}`: シンボルと文字列または文字列のベクトルのペアのベクトル

mapped_variables引数は次の形式を取ることができます：

1. `[:variable_name => "Plant"]`: Plantノードから1つの値を取得します
2. `[:variable_name => ["Leaf"]]`: Leafノードから値のベクトルを取得します
3. `[:variable_name => ["Leaf", "Internode"]]`: LeafおよびInternodeノードから値のベクトルを取得します
4. `[:variable_name => "Plant" => :variable_name_in_plant_scale]`: Plantノード内の別の変数名から1つの値を取得します
5. `[:variable_name => ["Leaf" => :variable_name_1, "Internode" => :variable_name_2]]`: 異なる名前のLeafおよびInternodeノードから値のベクトルを取得します
6. `[PreviousTimeStep(:variable_name) => ...]`: 変数を前のタイムステップの値で初期化するようにフラグを立て、依存グラフを構築するためには使用しません
7. `[:variable_name => :variable_name_from_another_model]`: 同じスケールの別のモデルから値を取得しますが、名前を変更します
8. `[PreviousTimeStep(:variable_name),]`: 変数をPreviousTimeStepとしてフラグを立て、依存グラフを構築するためには使用しません

さまざまな形式に関する詳細：

1. モデルの変数`variable_name`は、`Plant`ノードから取得されます。`Plant`シンボルを持つノードが1つだけ存在することを前提としています。

この場合、ステータスから利用可能な値はスカラーであり、ユーザーはMTG内に`Plant`型のノードが1つだけ存在することを保証する必要があります。

2. モデルの変数`variable_name`は、`Leaf`ノードから取得されます。ベクトルとして与えられているため、値はすべての`Leaf`型ノードから取得されます。モデルは値のベクトルを処理できる必要があります。たとえ`Leaf`型のノードが1つだけであっても、値は1要素のベクトルとして取得されます。
3. モデルの変数`variable_name`は、`Leaf`および`Internode`ノードから取得されます。値はすべての`Leaf`型および`Internode`型ノードから取得されます。
4. モデルの変数`variable_name`は、`Plant`ノード内の`variable_name_in_plant_scale`という変数から取得されます。これは、モデル内の変数名が取得元のスケールの変数名と異なる場合に便利です。
5. モデルの変数`variable_name`は、`Leaf`ノード内の`variable_name_1`という変数と、`Internode`ノード内の`variable_name_2`という変数から取得されます。
6. モデルの変数`variable_name`は、前のタイムステップで計算された値を使用します。これは、変数が依存グラフを構築するために使用されないことを意味します。

依存グラフは現在のタイムステップにのみ適用されるため、変数が自分自身に依存する場合の循環依存を回避するために使用されます。必要に応じて、ステータスで値を初期化できます。

7. モデルの変数`variable_name`は、同じスケールの別のモデルから取得されますが、別の変数名が付けられます。
8. モデルの変数`variable_name`は、単にPreviousTimeStep変数としてフラグが立てられ、依存グラフを構築するためには使用されません。

マッピングは値のコピーを作成せず、単に参照するだけであることに注意してください。これは、1つのノードのステータスで値が更新されると、他のノードでも更新されることを意味します。

# 例

```jldoctest mylabel
julia> using PlantSimEngine;
```

例のプロセスとモデルを含めます：

```jldoctest mylabel
julia> using PlantSimEngine.Examples;
```

モデルを取得しましょう：

```jldoctest mylabel
julia> model = ToyCAllocationModel()
ToyCAllocationModel()
```

モデルの変数と値が取得されるノードシンボルとの間のマッピングを定義することで、マルチスケールにすることができます：

たとえば、`carbon_allocation`が`Leaf`および`Internode`ノードから来る場合、次のようにマッピングを定義できます：

```jldoctest mylabel
julia> mapped_variables=[:carbon_allocation => ["Leaf", "Internode"]]
1-element Vector{Pair{Symbol, Vector{String}}}:
 :carbon_allocation => ["Leaf", "Internode"]
```

mapped*variables引数は、シンボルと文字列または文字列のベクトルのペアのベクトルです。この場合、`carbon*allocation`変数と`Leaf`および`Internode`ノードとの間のマッピングを定義するためのペアが1つだけあります。

次に、モデルとマッピングされた変数を`MultiScaleModel`コンストラクタに渡すことで、モデルをマルチスケールにすることができます：

```jldoctest mylabel
julia> multiscale_model = PlantSimEngine.MultiScaleModel(model, mapped_variables)
MultiScaleModel{ToyCAllocationModel, Vector{Pair{Union{Symbol, PreviousTimeStep}, Union{Pair{String, Symbol}, Vector{Pair{String, Symbol}}}}}}(ToyCAllocationModel(), Pair{Union{Symbol, PreviousTimeStep}, Union{Pair{String, Symbol}, Vector{Pair{String, Symbol}}}}[:carbon_allocation => ["Leaf" => :carbon_allocation, "Internode" => :carbon_allocation]])
```

マッピングされた変数とモデルにアクセスできます：

```jldoctest mylabel
julia> PlantSimEngine.mapped_variables_(multiscale_model)
1-element Vector{Pair{Union{Symbol, PreviousTimeStep}, Union{Pair{String, Symbol}, Vector{Pair{String, Symbol}}}}}:
 :carbon_allocation => ["Leaf" => :carbon_allocation, "Internode" => :carbon_allocation]
```

```jldoctest mylabel
julia> PlantSimEngine.model_(multiscale_model)
ToyCAllocationModel()
```
