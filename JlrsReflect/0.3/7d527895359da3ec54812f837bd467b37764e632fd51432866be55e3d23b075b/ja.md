```
reflect(types::Vector{<:Type}; f16::Bool=false, internaltypes::Bool=false)::Wrappers
```

`types`内のすべての型とその依存関係に対するRustラッパーを生成します。唯一の要件は、これらの型が型パラメータに依存するユニオンまたはタプルフィールドを含まないことです。ラッパーは、提供されたすべての型パラメータの内容を消去することによって、最も一般的なケースのために生成されるため、より適格な型を明示的に提供することでこの制限を回避することはできません。型を修飾することの唯一の効果は、使用されるパラメータのラッパーも生成されることです。ラッパーは、型パラメータを持たないビット型の場合、`Unbox`および`ValidLayout`、および`IntoJulia`を派生します。

一部の型は、`internal-types`機能が有効になっている場合にのみjlrsで利用可能です。この機能を有効にした場合、`internaltypes`キーワード引数を`true`に設定して、反映している型がそれらに依存している場合に提供されたラッパーを利用できます。同様に、`Float16`型は、jlrsで`f16`機能が有効になっていて、`f16`キーワード引数が`true`に設定されている場合にのみ反映できます。

この関数の結果はファイルに書き込むことができ、その内容は通常、有効なRustモジュールになります。

これらのラッパーをjlrsで使用する場合、これらの型は同じパスで利用可能でなければなりません。たとえば、`Main.Bar.Baz`のラッパーを生成する場合、この型はその正確なパスを通じて利用可能でなければならず、`Main.Foo.Bar.Baz`のような他のパスでは利用できません。

# 例

```jldoctest
julia> using JlrsReflect

julia> reflect([Complex])
#[repr(C)]
#[derive(Clone, Debug, Unbox, ValidLayout, ValidField, Typecheck)]
#[jlrs(julia_type = "Base.Complex")]
pub struct Complex<T>
where
    T: ::jlrs::layout::valid_layout::ValidField + Clone,
{
    pub re: T,
    pub im: T,
}
```
