```
@symbol_flagset T[::BaseType] flag_1[=bit_1] flag_2[=bit_2] ...
```

`T`という名前の`FlagSet{Symbol,BaseType}`サブタイプを作成し、提供されたフラグを持たせます。`T`の各インスタンスは、`{:flag1, :flag2, ...}`のサブセットを表します。関連する`bit_1`,`bit_2`などは、提供されている場合、異なる正の2の累乗でなければなりません。

次のコンストラクタが提供されています：     - `T(itr)`: 指定されたイテラブルオブジェクトからシンボルのセットを構築します。各シンボルは`:flag_1`, `:flag_2`などのいずれかでなければなりません；     - `T()`: 空のセットを構築します；     - `T(sym1::Symbol, syms::Symbol...)`: `T([sym1, syms...])`と同等です；     - `T(bitmask::Integer)`: マスク内の各ビットに関連付けられたフラグのセットを構築します；     - `T(; kwargs...)`: 各`flag_i`はブール値として提供できます     (`flag_i = true`は`:flag_i`を含み、`flag_i = false`はそれを除外します)。

新しいコンストラクタメソッドや提供されたメソッドのオーバーライドを安全に行うことができます（内部構造体を使用するデフォルトを除く、すなわち`T(::FlagSets.BitMask)`）。

非`Symbol`定数のセットを構築するには、マクロ[`@flagset`](@ref)を使用します。

# 例

```julia
julia> @symbol_flagset FontFlags bold=1 italic=2 large=4

julia> FontFlags(1)
FontFlags with 1 element:
  :bold

julia> FontFlags(:bold, :italic)
FontFlags with 2 elements:
  :bold
  :italic

julia> FontFlags(bold=true, italic=false)
FontFlags with 1 element:
  :bold

julia> for flag in FontFlags(3); println(flag) end
bold
italic

julia> FontFlags(3) | FontFlags(4)
FontFlags with 3 elements:
  :bold
  :italic
  :large

julia> eltype(FontFlags)
Symbol

julia> typemax(FontFlags)
FontFlags with 3 elements:
  :bold
  :italic
  :large

julia> typemin(FontFlags)
FontFlags([])
```

値は`begin`ブロック内でも指定できます。例えば：

```julia
@symbol_flagset T begin
    flag_1 [= x]
    flag_2 [= y]
end
```

`BaseType`が提供されている場合、それは各`bit_i`を表すのに十分な`Integer`型でなければなりません。そうでない場合、便利な整数型が推測されます（Cコードとの互換性を保証するために`UInt32`が可能であれば使用されます）。`T`の各インスタンスは`BaseType`に変換でき、変換された`BaseType`内の各ビットがフラグセット内のフラグに対応します。`read`と`write`はこれらの変換を自動的に行います。非デフォルトの`BaseType`でフラグセットが作成された場合、`Integer(flagset)`は`BaseType`型の整数`flagset`を返します。

```julia
julia> convert(Int, FontFlags(bold=true, italic=false))
1

julia> convert(Integer, FontFlags(bold=true, italic=false))
0x00000001
```

フラグセット型またはインスタンスのフラグをリストするには、`flags`を使用します。例えば：

```julia
julia> flags(FontFlags)
(:bold, :italic, :large)

julia> flags(FontFlags(3))
(:bold, :italic)
```
