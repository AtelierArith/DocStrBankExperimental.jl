An [`Abbreviation`](@ref) for including the function name matching the method of the docstring.

# 使用法

これは、ユーザーが引数リストの完全な制御を保持したい場合や、後者が存在しない場合（例えば、汎用関数）に、ドキュメント文字列内で関数名を繰り返さないために主に便利です。

生成されたドキュメント文字列のスニペットは引用されていないことに注意してください。インデントまたは明示的な引用を使用してください。

# 例

```julia
"""
    $(FUNCTIONNAME)(d, θ)

Calculate the logdensity `d` at `θ`.

Users should define their own methods for `FUNCTIONNAME`.
"""
function logdensity end
```
