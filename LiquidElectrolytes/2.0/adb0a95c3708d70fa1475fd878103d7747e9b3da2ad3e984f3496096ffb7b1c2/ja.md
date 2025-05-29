```
update_derived!(electrolyte::ElectrolyteData)
```

派生電解質データを更新します。これは、他のいくつかのパラメータを変更した後に、`ElectrolyteData`のフィールド`Mrel`、`vrel`、`barv`、`tildev`、`RT`、`γ_bulk`を更新するために呼び出す必要があります。

渡された電解質データは、[`PNPSystem`](@ref)、[`PBSystem`](@ref)、[`dlcapsweep`](@ref)、[`ivsweep`](@ref)、[`cvsweep`](@ref)によって呼び出されます。
