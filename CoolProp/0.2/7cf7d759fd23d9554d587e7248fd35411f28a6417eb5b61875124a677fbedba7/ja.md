```
set_reference_state(ref::AbstractString, reference_state::AbstractString)
```

文字列表現に基づいて参照状態を設定します。

#引数

  * `fluid::AbstractString`	流体の名前（バックエンドは "REFPROP::Water" のように提供できます。バックエンドが提供されない場合は "HEOS" が仮定されます）
  * `reference_state::AbstractString`	使用する参照状態、次のいずれか：

| 参照状態     | 説明                                    |
|:-------- |:------------------------------------- |
| "IIR"    | h = 200 kJ/kg, s=1 kJ/kg/K at 0C 飽和液体 |
| "ASHRAE" | h = 0, s = 0 @ -40C 飽和液体              |
| "NBP"    | h = 0, s = 0 @ 1.0 bar 飽和液体           |
| "DEF"    | 流体のデフォルト参照状態にリセット                     |
| "RESET"  | オフセットを削除                              |

#例

```julia
julia> h0=-15870000.0; # J/kg
julia> s0= 3887.0; #J/kg
julia> rho0=997.1;
julia> T0=298.15;
julia> M = PropsSI("molemass", "Water");
julia> set_reference_stateD("Water", T0, rho0/M, h0*M, s0*M);
julia> PropsSI("H", "T", T0, "P", 101325, "Water")
-1.5870107493843542e7
julia> set_reference_stateS("Water", "DEF");
julia> PropsSI("H", "T", T0, "P", 101325, "Water")
104920.1198093371
```

#Ref set*reference*stateS(const std::string& FluidName, const std::string& reference_state)

#注意 参照状態の変更はプログラムの初期化の一部であるべきであり、計算中に参照状態を変更することは推奨されません。
