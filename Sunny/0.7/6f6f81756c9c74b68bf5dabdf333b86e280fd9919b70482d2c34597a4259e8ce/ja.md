```
to_inhomogeneous(sys::System)
```

非同次相互作用を許可するシステムのコピーを返します。これは、[`set_onsite_coupling_at!`](@ref)、[`set_exchange_at!`](@ref)、および[`set_vacancy_at!`](@ref)を使用して設定できます。

非同次システムは、相互作用の対称性伝播やシステムの再形成をサポートしていません。
