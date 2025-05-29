```
@flagset T [key_1 =] [bit_1 -->] flag_1 [key_2 =] [bit_2 -->] flag_2...
```

名前 `T` の [`FlagSet`](@ref) サブタイプを作成し、提供されたフラグを評価します。作成された型の各インスタンスは、`{flag_1, flag_2, ...}` のサブセットを表します。関連する `bit_1`, `bit_2` などが提供されている場合、それらは異なる正の2の累乗でなければなりません。

次のコンストラクタが提供されています：     - `T(itr)`: 指定されたイテラブルオブジェクトからフラグのセットを構築します。各フラグは `flag_1`, `flag_2` などのいずれかでなければなりません；     - `T()`: 空のセットを構築します；     - `T(bitmask::Integer)`: `mask` の各ビットに関連付けられたフラグのセットを構築します；     - `T(; kwargs...)`: 各 `key_i` はブール値を持つキーワードとして指定できます（`key_i = true` は `flag_i` を含め、`key_i = false` は除外します）。

新しいコンストラクタメソッドや、提供されたメソッドのオーバーライドを安全に行うことができます（内部構造体 `FlagSets.BitMask` に対して定義されたデフォルトを除く）。

# 例

```julia
julia> @flagset RoundingFlags begin
    down = RoundDown
    up = RoundUp
    near = 16 --> RoundNearest
    64 --> RoundNearestTiesUp  # キーなし
end

julia> RoundingFlags([RoundDown,RoundUp])
RoundingFlags with 2 elements:
  RoundingMode{:Down}()
  RoundingMode{:Up}()

julia> RoundingFlags(near = true, up = false, RoundNearestTiesUp = true)
RoundingFlags with 2 elements:
  RoundingMode{:Nearest}()
  RoundingMode{:NearestTiesUp}()

julia> RoundingFlags(1)
RoundingFlags with 1 element:
  RoundingMode{:Down}()

julia> for flag in RoundingFlags(3); println(flag) end
RoundingMode{:Down}()
RoundingMode{:Up}()

julia> RoundingFlags(3) | RoundingFlags(16)
RoundingFlags with 3 elements:
  RoundingMode{:Down}()
  RoundingMode{:Up}()
  RoundingMode{:Nearest}()

julia> eltype(RoundingFlags)
RoundingMode

julia> typemax(RoundingFlags)
RoundingFlags with 4 elements:
  RoundingMode{:Down}()
  RoundingMode{:Up}()
  RoundingMode{:Nearest}()
  RoundingMode{:NearestTiesUp}()

julia> typemin(RoundingFlags)
RoundingFlags([])
```

もし `flag_i` が `Symbol` であり、`key_i` が明示的に与えられていない場合、`key_i` は `flag_i` に設定されます。したがって、以下の2つのマクロは等価です：

```
@flagset FontFlags :bold :italic 8 --> :large
@flagset FontFlags begin
    bold = :bold
    italic = :italic
    large = 8 --> :large
end
```

次の構文を使用して `FlagType` および/または `BaseType` を提供できます：

```julia
@flagset T {FlagType,BaseType} ... # 提供された型を使用
@flagset T {FlagType} ...          # BaseTypeを検出
@flagset T {FlagType,_} ...        # BaseTypeも検出
@flagset T {_,BaseType} ...        # FlagTypeを検出
@flagset T {} ...                  # 中括弧は無視されます
```

`FlagType` が提供されていない場合、または `_` の場合、フラグ値から推測されます（配列コンストラクタが行うように）。そうでない場合、`flag_1`, `flag_2` などは `FlagType` の型でなければなりません。

`BaseType` が提供されていない場合、または `_` の場合、便利な整数型が推測されます（最大のCコードとの互換性のために `UInt32` が使用されます）。そうでない場合、各 `bit_i` を表すのに十分な大きさの `Integer` 型でなければなりません。

各 `T` のインスタンスは `BaseType` に変換でき、変換された `BaseType` で設定された各ビットはフラグセット内のフラグに対応します。`read` と `write` はこれらの変換を自動的に行います。非デフォルトの `BaseType` でフラグセットが作成された場合、`Integer(flagset)` は `BaseType` 型の整数 `flagset` を返します。

```julia
julia> convert(Int, RoundingFlags(up = true, near = true))
6

julia> convert(Integer, RoundingFlags(up = true, near = true))
0x00000006
```

フラグセット型またはインスタンスのフラグをリストするには、`flags` を使用します。例えば：

```julia
julia> flags(RoundingFlags)
(RoundingMode{:Down}(), RoundingMode{:Up}(), RoundingMode{:Nearest}())

julia> flags(RoundingFlags(3))
(RoundingMode{:Down}(), RoundingMode{:Up}())
```

!!! note
    後方互換性のため、構文 `@flagset T::BaseType ...` は `@symbol_flagset T::BaseType ...` と同等ですが、前者の構文は非推奨です（代わりに [`symbol_flagset`](@ref) を使用してください）。

