```
add_variable!(database::TelemetryDatabase, label::Symbol, position::Integer, size::Integer, tf::Function, btf::Function = default_bit_transfer_function, rtf::Function = default_raw_transfer_function; kwargs...) -> Nohting
```

`database`に変数を追加します。

# 引数

  * `database::TelemetryDatabase`: データベース。
  * `label::Symbol`: データベース内の変数ラベル。
  * `position::Int`: テレメトリデータベース内の変数の位置。
  * `size::Int`: 変数のサイズ。
  * `tf::Function`: 変数の転送関数。詳細については、セクション `Transfer   function` を参照してください。
  * `btf::Function`: 変数のビット転送関数。   (**デフォルト** = `default_bit_transfer_function`)
  * `rtf::Function`: 変数の生転送関数。   (**デフォルト** = `default_raw_transfer_function`)

!!! note
    変数が他の変数の処理された値のみから取得される場合、`position` と `size` は省略できます。この場合、キーワード `dependencies` は `Nothing` であってはなりません。


# キーワード

  * `alias::Union{Nothing, Symbol}`: 変数のエイリアス。この場合、関数   [`get_variable_description`](@ref) は検索時にこのエイリアスも考慮します。   (**デフォルト** = `nothing`)
  * `default_view::Symbol`: 処理中にこの変数のデフォルトビューを選択します。 利用可能なオプションのリストについては、[`process_telemetries`](@ref) を参照してください。   (**デフォルト** = `:processed`)
  * `dependencies::Union{Nothing, Vector{Symbol}}`: この変数の処理された値を取得するために必要な依存関係のリストを含むベクター。 `nothing` の場合、変数には依存関係がありません。 (**デフォルト** = `nothing`)
  * `description::String`: 変数に関する説明。
  * `endianess::Symbol`: 変数のエンディアンを示す `:littleendian` または `:bigendian`。 (**デフォルト** = `:littleendian`)

# ビット転送関数

ビット転送関数は次のシグネチャを持つ必要があります：

```julia
function btf(frame::AbstractVector{UInt8})::AbstractVector{UInt8}
```

その目的は、テレメトリから `frame` を取得し、現在のテレメトリ変数に関連するビットに処理することです。 `frame` は、変数パラメータ `position`、`size`、および `endianess` から取得されたバイトのセットです。

# 生転送関数

生転送関数の目的は、`btf` で作成されたテレメトリ `byte_array` を取得し、生の値に処理することです。この値は、変数の処理されたデータを取得するために転送関数で使用されます。

生転送関数は次のいずれかのシグネチャを持つことができます：

```julia
function rtf(byte_array::AbstractVector{UInt8})
```

または

```julia
function rtf(byte_array::AbstractVector{UInt8}, processed_variables::Dict{Symbol, Any})
```

# 転送関数

変数の転送関数は次のいずれかのシグネチャを持つことができます：

```julia
function tf(raw::Any)
```

生の情報 `raw` を与えられた場合の変数の処理された値を返します。生転送関数から取得されます。

```julia
function tf(raw::Any, processed_variables::Dict{Symbol, Any})
```

生の情報 `raw` を与えられた場合の変数の処理された値を返します。生転送関数から取得され、`processed_variables` にある処理された変数のセットが含まれます。このシグネチャは、転送関数が他の変数に依存する場合に使用する必要があります。
