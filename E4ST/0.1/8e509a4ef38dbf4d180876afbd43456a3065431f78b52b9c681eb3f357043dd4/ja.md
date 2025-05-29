```
抽象型 Modification
```

Modificationは、モデルに変更を加えるための抽象型を表します。

`Modification`はE4STの動作を変更する方法を表します。`Modifications`のいくつかの可能な例（必ずしも実装されているわけではありません）には、以下が含まれます：

  * 各年のNG価格をスケールする
  * コロラド州の炭素排出量に上限を設ける
  * 目標とベンチマークレートが変化する全国的なCESを追加する
  * PJMに新しい原子力発電を追加するのを防ぐ
  * カスタム計算結果をファイルにログする
  * 結果処理の一環として州ごとの排出量のヒートマップをプロットして保存する
  * 空は限界なし！

## `Modification`の定義

具体的な`Modification`型を定義する際には、以下のことを知っておく必要があります。

  * ModificationsはYAML構成ファイルで指定されるため、`Modification`はキーワード引数で構築する必要があります。`Base.@kwdef`が役立つかもしれません。
  * すべての`Modification`は構成ファイル内の名前とペアになっています。その名前は、型に`name`フィールドがある場合、`Modification`コンストラクタにキーワード引数として自動的に渡されます。`name`は`Symbol`として渡されます。

`Modification`は最大4つの場所で変更を加えることができ、メソッドのデフォルトの動作は変更を加えないことです：

  * [`modify_raw_data!(mod, config, data)`](@ref) - データ準備ステップで、[`read_data_files!(config, data)`](@ref)の直後、データを設定する前
  * [`modify_setup_data!(mod, config, data)`](@ref) - データ準備ステップで、[`setup_data!(config, data)`](@ref)の直後、`Model`を設定する前
  * [`modify_model!(mod, config, data, model)`](@ref) - モデル設定ステップで、DC-OPFを設定した後、最適化する前
  * [`modify_results!(mod, config, data)`](@ref) - モデルを最適化した後、結果生成ステップで

Modificationsは、`run_e4st`の呼び出しの最初に構成ファイルが保存されるときにYAMLに印刷されます。すべてのフィールドを印刷することが望ましくないModificationを実装する場合は、次のインターフェースを実装できます：

  * [`fieldnames_for_yaml(::Type)`](@ref) - 希望するフィールド名を`Symbol`のコレクションとして返します

Modificationにはランクを付けることができ、モデルを変更する際に呼び出される順序を決定します。これは、modが前のmodで計算された情報を必要とする場合や、別のmodの上に適用する必要がある場合に重要です。ランクは、[`mod_rank(::Type{<:Modification})`](@ref)のメソッドを定義することで指定されます。デフォルトのランクは0です。`CCUS`や`DCLines`のようなデータとモデルの機能を設定するModificationは、呼び出される前を示すために負の値を持つことができますが、政策のようなmodは、設定modの後にモデルを変更することを意味する正のランクを持ちます。

## 構成ファイルYAMLでの`Modification`の指定

`Modifications`は構成ファイルで指定する必要があります。型キーと、コンストラクタ内の他の希望するキーワード引数のキーを持っている必要があります。

## 例

CSVファイルのテーブルに基づいて天然ガスの価格を変更するModificationを作成したいとします。

```julia
using E4ST, CSV, DataFrames
struct UpdateNGPrice <: Modification
    filename::String
    prices::DataFrame
end

# キーワード引数コンストラクタを定義
function UpdateNGPrice(; filename=nothing)
    filename === nothing && error("UpdateNGPriceにはファイル名を提供する必要があります")
    prices = CSV.read(filename, DataFrame)
    return UpdateNGPrice(filename, prices)
end

# YAMLが全体の価格テーブルを印刷しないようにする
function E4ST.fieldnames_for_yaml(::Type{UpdateNGPrice})
    return (:filename,)
end

function E4ST.modify_raw_data!(mod::UpdateNGPrice, config, data)
    # ここでmod.pricesから天然ガスの価格を更新します
end
```

これを構成ファイルの`mods`リストに追加するには：

```yaml
mods:
  ...                                   # 必要に応じて他のmods
  update_ng_price:                      # これはmodの名前です
    type: UpdateNGPrice
    filename: "C:/path/to/file.csv"
  ...                                   # 必要に応じて他のmods
```
