```
@exception(macro_name::Symbol, args::Union{Symbol, Expr}...; context::Expr=:()) -> Expr
```

例外を作成するためのマクロを作成します。オプションで、構造体を定義する前にコンテキストを注入します。

# 引数

  * `macro_name::Symbol`: マクロの名前
  * `args::Tuple{Vararg{Union{Symbol, Expr}}}`: 例外構造体に定義されるフィールドのセット

# キーワード

  * `context::Expr=:()`: 例外構造体を定義する前に評価される式

# 戻り値

  * `Expr`: 新しいマクロ定義

# 例外

  * [`OnlyOneEquation`](@ref): 1つ以上の方程式が渡された

# 例

```jldoctest; output = false
using Exceptions
using Suppressor
using SyntaxTree

macro_name = :name
args = (:(arg1::String), :(arg2))
context = :()

EXCEPTIONS = Dict{Symbol, Any}()
EXCEPTIONS[:DocstringIsNotAString] = Exceptions.Internal.DocstringIsNotAString
EXCEPTIONS[:ErrorMessageIsNotAString] = Exceptions.Internal.ErrorMessageIsNotAString

d1 = @capture_out(
    @macroexpand(@exception(name, arg1::String, arg2)) |> linefilter! |> dump
)

d2 = @capture_out quote
    macro $(macro_name)(
        exception_name::Symbol,
        docstring::Union{Expr, String},
        error_message_bits::Union{Expr, String, Char}...,
    )
        args = $(args)

        error_header = "$(__module__).$(exception_name):"
        error_message_bits = ("\n\n$(error_header)\n", error_message_bits..., '\n')

        $(context)

        EX = $(EXCEPTIONS)
        error_message_bits_filtered = filter(
            e -> typeof(e) == String || e.head ≠ :(.) && e.args[1] ≠ :(e),
            error_message_bits,
        )

        return esc(
            quote
                # チェック
                if !($(docstring) isa String)
                    throw($(EX[:DocstringIsNotAString])())
                end
                if !(string($(error_message_bits_filtered...)) isa String)
                    throw($(EX[:ErrorMessageIsNotAString])())
                end

                @doc $(docstring)
                mutable struct $(exception_name) <: Exception
                    $(args...)
                end

                Base.showerror(io::IO, e::$(exception_name)) =
                print(io, $(error_message_bits...))
            end
        )
    end
end |> linefilter! |> dump

d1 == d2

# 出力

true
```
