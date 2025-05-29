```
@stable [options...] [code_block]
```

関数の型の安定性を強制するためのマクロです。適用されると、関数の戻り値の型が具体的であることを保証します。型の不安定性が検出されると、`TypeInstabilityError`がスローされます。

# オプション

  * `default_mode::String="error"`:

      * デフォルトモードを`"error"`から`"warn"`に変更すると、警告のみを発生させるか、`"disable"`にして型の不安定性チェックをデフォルトで無効にします。
      * DispatchDoctorを使用するパッケージのモードをローカルまたはグローバルにオーバーライドするには、LocalPreferences.tomlの`"dispatch_doctor_mode"`キーを使用できます（通常はPreferences.jlで設定されます）。
  * `default_codegen_level::String="debug"`:

      * コード生成レベルを`"min"`に設定すると、各安定化された関数のために単一の関数本体のみが生成されます。デフォルトの`"debug"`は、`@code_warntype`が使用できるように、全体の重複関数を生成します。
      * DispatchDoctorを使用するパッケージのコード生成レベルをローカルまたはグローバルにオーバーライドするには、LocalPreferences.tomlの`"dispatch_doctor_codegen_level"`キーを使用できます。
  * `default_union_limit::Int=1`:

      * 安定と見なされるユニオン内の最大要素数を設定します。デフォルトは`1`で、すべてのユニオンが不安定と見なされます。`2`の値は、`Union{Float32,Float64}`が安定と見なされることを示しますが、`Union{Float16,Float32,Float64}`はそうではありません。
      * DispatchDoctorを使用するパッケージのユニオン制限をローカルまたはグローバルにオーバーライドするには、LocalPreferences.tomlの`"dispatch_doctor_union_limit"`キーを使用できます。

# 例

```julia
using DispatchDoctor: @stable

@stable function relu(x)
    if x > 0
        return x
    else
        return 0.0
    end
end
```

これは自動的に型の不安定性をフラグ付けします：

```julia
julia> relu(1.0)
1.0

julia> relu(0)
ERROR: TypeInstabilityError: Instability detected in function `relu`
with arguments `(Int64,)`. Inferred to be `Union{Float64, Int64}`,
which is not a concrete type.
```

# 拡張ヘルプ

`@stable`を`begin`や`module`などの任意のコードブロックに適用し、すべての関数に適用することもできます。（ただし、これはクロージャ関数をスキップします。）

```julia
using DispatchDoctor: @stable

@stable begin
    f(x) = x
    g(x) = x > 0 ? x : 0.0
    @unstable begin
        g(x::Int) = x > 0 ? x : 0.0
    end
    module A
        h(x) = x
        include("myfile.jl")
    end
end
```

この`@stable`は`f`、`g`、`h`、および`myfile.jl`内のすべての関数に適用されます。`g(x::Int)`の定義はスキップされるため、`g`に`Int`入力が提供されるとき、型の不安定性は検出されません。 ```
