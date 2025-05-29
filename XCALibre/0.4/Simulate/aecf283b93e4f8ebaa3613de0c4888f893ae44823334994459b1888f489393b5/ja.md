```
@kwdef struct Configuration{SC,SL,RT,HW}
    schemes::SC
    solvers::SL
    runtime::RT
    hardware::HW
end
```

`Configuration`型はすべてのフローソルバーに渡され、シミュレーションを実行するためのすべての関連情報を提供します。

# 入力

  * `schemes::NamedTuple` このキーワード引数は、フローソルバーに離散化スキーム情報を渡すために使用されます。詳細については、[Numerical setup](@ref)を参照してください。
  * `solvers::NamedTuple` このキーワード引数は、各フィールド情報の線形ソルバーの設定をフローソルバーに渡すために使用されます。詳細については、[Runtime and solvers](@ref)を参照してください。
  * `runtime::NamedTuple` このキーワード引数は、フローソルバーにランタイム情報を渡すために使用されます。詳細については、[Runtime and solvers](@ref)を参照してください。
  * `hardware::NamedTuple` このキーワード引数は、フローソルバーにハードウェア設定とバックエンド設定を渡すために使用されます。詳細については、[Pre-processing](@ref)を参照してください。

# 例

```julia
config = Configuration(
    solvers=solvers, schemes=schemes, runtime=runtime, hardware=hardware)
```
