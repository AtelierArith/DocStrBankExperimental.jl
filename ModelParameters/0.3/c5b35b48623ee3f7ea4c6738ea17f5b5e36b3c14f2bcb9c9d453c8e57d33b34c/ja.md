# ModelParameters

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://rafaqz.github.io/ModelParameters.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://rafaqz.github.io/ModelParameters.jl/dev) [![CI](https://github.com/rafaqz/ModelParameters.jl/workflows/CI/badge.svg)](https://github.com/rafaqz/ModelParameters.jl/actions?query=workflow%3ACI) [![Coverage](https://codecov.io/gh/rafaqz/ModelParameters.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/rafaqz/ModelParameters.jl)

ModelParametersは、モデルの構造と構成に関する技術的な決定を使いやすさの懸念から切り離し、複雑で高性能なモデルの作成と使用のプロセスを簡素化します。

パラメータの線形インデックス、Tables.jlインターフェース、および制御可能なInteract.jlインターフェース（InteractModels.jl経由）を提供します - どんなオブジェクトでも、どんな複雑さでも。不変オブジェクトのパラメータは、ベクトル、タプル、またはテーブルから単一のコマンドを使用して更新でき、新しい値でオブジェクトを再構築します。

## 使用例

ModelParameters.jlは、異種構造と複数の定式化オプションを持つ物理/環境/生態モデルの作成を支援するように設計されています。

これらのモデルが特定の複雑さを超えると、モジュール方式で整理し、他のモデルのバリアントでコンポーネントを再利用することが好ましくなります。このパターンは、CLIMAプロジェクトに関連する気候モデルや土地モデル、またこのパッケージが構築されたDynamicGrids.jlやGrowthMaps.jlのような生態モデリングツールに見られます。

モデルは、構造体の合成されたネストされた階層、オブジェクトの`Tuple`チェーン、`NameTuple`、または上記のいずれかの組み合わせとして構成できます。パフォーマンスやGPUでの実行のために、不変性がしばしば必要です。

問題は、これらのモデルをOptim.jlで使用しようとしたり、DiffEqSensitivity.jlで感度分析を実行したり、ベイズモデリングパッケージに事前分布を渡そうとしたときに発生します。これらのパッケージは、しばしばパラメータ値、境界、および事前分布を`Vector`として必要とします。また、必要に応じて新しいパラメータでモデルを更新する必要がある場合もあります。すべてのモデルの組み合わせに対してこれらの変換を書くことは、エラーが発生しやすく、非効率的です - 特に、パラメータを変更するために再構築する必要があるネストされた不変モデルでは。

ModelParameters.jlは、構造体、`Tuple`、および`NamedTuple`で構築された任意に複雑なモデルを、値、境界、事前分布、および必要なその他のもののベクトルに変換し、更新時に全体のモデルを簡単に再構築できます。これは、モデル内のどこにあってもパラメータを`Param`でラップすることで実現されます：

```julia
using ModelParameters

Base.@kwdef struct Submodel1{A,B}
    α::A = Param(0.8, bounds=(0.2, 0.9))
    β::B = Param(0.5, bounds=(0.7, 0.4))
end

Base.@kwdef struct Submodel2{Γ}
    γ::Γ = Param(1e-3, bounds=(1e-4, 1e-2))
end

Base.@kwdef struct SubModel3{Λ,X}
    λ::Λ = Param(0.8, bounds=(0.2, 0.9))
    x::X = Submodel2()
end

julia> model = Model((Submodel1(), SubModel3()))
Model with parent object of type: 

Tuple{Submodel1{Param{Float64,NamedTuple{(:val, :bounds),Tuple{Float64,Tuple{Float64,Float64}}}},Param{Float64,NamedTuple{(:val, :bounds),Tuple{Float64,Tuple{Float64,Float64}}}}},SubModel3{Param{Float64,NamedTuple{(:val, :bounds),Tuple{Float64,Tuple{Float64,Float64}}}},Submodel2{Param{Float64,NamedTuple{(:val, :bounds)
,Tuple{Float64,Tuple{Float64,Float64}}}}}}}

And parameters:
┌───────────┬───────┬───────┬────────────────┐
│ component │ field │   val │         bounds │
├───────────┼───────┼───────┼────────────────┤
│ Submodel1 │     α │   0.8 │     (0.2, 0.9) │
│ Submodel1 │     β │   0.5 │     (0.7, 0.4) │
│ SubModel3 │     λ │   0.8 │     (0.2, 0.9) │
│ Submodel2 │     γ │ 0.001 │ (0.0001, 0.01) │
└───────────┴───────┴───────┴────────────────┘

julia> model[:val]
(0.8, 0.5, 0.8, 0.001)
```

Optim.jlのためにモデルの値をベクトルとして取得するには、単に：

```julia
collect(model[:val])
```

## Paramsとは？

`Param`は、パラメータ値とそれに関するメタデータを追跡するためのラッパーです。`Param`は柔軟なフィールドを持っていますが、常に`:val`フィールドを持つことが期待されています - これはキーワード引数を使用しない場合のデフォルトです：

```julia
par = Param(99.0)
@assert par.val == 99.0
```

内部的に`Param`は、スクリプトの柔軟性のために`NamedTuple`を使用します。必要なフィールドを追加するだけです。パラメータが`Model`に組み込まれると、すべてのフィールドが標準化され、ギャップは`nothing`で埋められます。

特定の動作を持つ「特権」フィールドがいくつかあります。`units`フィールドは、他のフィールドと`withunits`を使用して結合され、実際に`units`フィールドがある場合、モデルで`stripparams`を実行するときに`val`に対してデフォルトで行われます。サブパッケージInteractModels.jlの`InteractModel`は、`range`または`bounds`フィールドを`units`と結合し、スライダーを構築するために使用することもあります。

`Param`はまた`Number`でもあり、便利さのために多くのモデルでそのまま機能するはずです。しかし、`stripparams`を使用してオブジェクトから簡単に削除できます。

## モデルとは？

モデルは、全体のモデルのための別のラッパータイプであり、何であれ構いません。これは、型指定された不変モデルのための可変で型指定されていないコンテナであり、ユーザーインターフェースで更新したり、`setproperties!`を使用して更新したりできます。更新されたバージョンへのハンドルを保持できます。`Model`は、Tables.jlインターフェースを提供し、REPLでパラメータのテーブルを提供し、モデルに変更を加えるための強力なツールを提供します。

最大のパフォーマンスが必要で、モデルオブジェクトへのハンドルが必要ない場合は、より制限された`StaticModel`バリアントがあります。

InteractModels.jlサブパッケージの`InteractModel`は、`Model`と同一ですが、Interact.jlインターフェースが追加されています。これは、生成されたスライダーで行ったモデルパラメータの変更に応じて、ウェブページに表示できるプロットなどを生成する関数を受け入れます。

## モデル値の設定

### 新しい値の設定

モデルからすべてのモデルパラメータに新しい列を直接追加することもできます：

```julia
model[:bounds] = ((1.0, 4.0), (0.0, 1.0), (0.0, 0.1), (0.0, 100.0))
```

### 数値型の入れ替え

ModelParametersは、モデルパラメータの変更を非常に簡単にします。すべてのモデル値を`Float32`に更新するには、単に次のようにします：

```julia
model[:val] = map(Float32, model[:val])
```

## Tables.jlインターフェース

Tables.jlインターフェースを使用して、モデルパラメータをCSVまたは他の種類のテーブルや`DataFrame`に保存およびインポートすることもできます：

```julia
update!(model, table)
```

## ライブInteract.jlモデル

InteractModels.jlはModelParameters.jlのサブパッケージですが、別途インストールする必要があります。これにより、必要ないときにInteract.jlの重いウェブスタック依存関係を読み込むことを避けます。

InteractModelsを使用すると、任意のモデルに対して自動的にInteract.jlウェブインターフェースを定義できます。これは、モデルをウェブページに表示できる方法でプロットまたは表示する関数を提供することによって実現されます。インターフェース、スライダーコントローラー、およびモデルの更新はすべて処理されます。

## 潜在的な問題

フィールドに接続されていない型パラメータを持つ構造体を定義すると、ModelParameters.jlは新しい`Param`値でそれらを再構築したり、`stripparams`を使用して`Param`ラッパーを削除したりできません。

これに対する解決策は、[ConstructionBase.jl](https://github.com/JuliaObjects/ConstructionBase.jl)から`ConstructionBase.constructorof`を定義することであり、これにより、Flatten.jl、Setfield.jl、Accessors.jl、BangBang.jlなどの不変操作のための他のパッケージと一緒にオブジェクトを使用できるようになります。

[ConstructionBaseExtras.jl](https://github.com/JuliaObjects/ConstructionBaseExtras.jl)も、StaticArrays.jl配列などの一般的なパッケージへのサポートを追加するために存在します。StaticArraysのサポートが必要な場合はインポートするか、追加のパッケージへのサポートを追加するための問題を開いてください。
