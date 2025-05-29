```
@exception(macro_name::Symbol, args::Union{Symbol, Expr}...; context::Expr=:()) -> Expr
```

Create a macro to create exceptions. Optionally inject context before defining the structure.

# Arguments

  * `macro_name::Symbol`: name of the macro
  * `args::Tuple{Vararg{Union{Symbol, Expr}}}`: a set of fields to be defined in the exception structure

# Keywords

  * `context::Expr=:()`: expression evaluated before defining the exception structure

# Returns

  * `Expr`: new macro definition

# Throws

  * [`OnlyOneEquation`](@ref): more than one equation has been passed

# Example

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
                # Checks
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

# output

true
```
