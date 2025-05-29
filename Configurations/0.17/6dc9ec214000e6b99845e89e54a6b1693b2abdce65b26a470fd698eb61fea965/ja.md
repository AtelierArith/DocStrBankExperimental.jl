```
@option [alias::String] <struct def>
```

オプション構造体タイプを定義します。これにより、指定された `Dict{String}` オブジェクト（キーは `String` 型でなければなりません）を定義した構造体タイプのインスタンスにパースするメソッドが自動生成されます。`alias` 文字列を使用して、同じフィールドに対する複数の可能なオプションタイプを区別できます。

# 特殊タイプ

  * `Maybe{T}`: このタイプは `Union{Nothing, T}` と同等であり、`@option` では特別に扱われ、指定されていない場合は常にデフォルト値 `nothing` を持ちます。
  * [`Reflect`](@ref): このタイプは、対応する型情報を格納するためにフィールドを使用できるように特別に扱われます。

!!! compat "Configurations 0.16"
    v0.16.0 から、Configurations は `Base.show` メソッドのオーバーロードを自動的に行わなくなります。オプションタイプのきれいな印刷が必要な場合は、[GarishPrint](https://github.com/Roger-luo/GarishPrint.jl) によって提供される `Base.show(io::IO, mime::MIME, x)` メソッドを `pprint_struct(io, mime, x)` にオーバーロードすることを検討してください。


!!! compat "Configurations 0.12"
    v0.12.0 から、フィールドエイリアス機能はフィールドのドキュメント文字列との構文の競合のために削除されました。詳細は [#17](https://github.com/Roger-luo/Configurations.jl/issues/17) を参照してください。


# 例

エイリアスの有無にかかわらず、`@option` マクロを使用してオプションタイプを定義できます。

```julia-repl
julia> "Option A"
       @option "option_a" struct OptionA
           name::String
           int::Int = 1
       end

julia> "Option B"
       @option "option_b" struct OptionB
           opt::OptionA = OptionA(;name = "Sam")
           float::Float64 = 0.3
       end
julia> option = from_dict(OptionB, d)
OptionB(;
    opt = OptionA(;
        name = "Roger",
        int = 2,
    ),
    float = 0.33,
)
```

1つのフィールドに対して複数の可能なオプションタイプがある場合、エイリアスを使用してそれらを区別できます。

```julia-repl
julia> @option struct OptionD
           opt::Union{OptionA, OptionB}
       end

julia> d1 = Dict{String, Any}(
               "opt" => Dict{String, Any}(
                   "option_b" => d
               )
           );

julia> from_dict(OptionD, d1)
OptionD(;
    opt = OptionB(;
        opt = OptionA(;
            name = "Roger",
            int = 2,
        ),
        float = 0.33,
    ),
)
```
