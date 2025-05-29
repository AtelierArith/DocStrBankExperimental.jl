```
abstract type MoleGas{M,μ,Tμ,k,Tk} <: AbstractMole{M} end
```

モルガス物質は、モル質量 `M` とサザーランド定数 `μ,Tμ,k,Tk` によって指定されます。適用可能な場合、追加の導出値 `wavenumber`、`wavelength`、`frequency`、`vibration` および `AbstractMole` 値に関連する継承定数を誘発します。
