```
is_osi_approved(spdx_identifier::String) -> Bool
is_osi_approved(nt::NamedTuple) -> Bool
```

[SDPX 3.10 identifier](https://spdx.dev/ids/) が [OSI approved](https://opensource.org/licenses) であるかどうかを、自動生成されたリストと照らし合わせて確認するか、`licenses_found` キーを持つ `NamedTuple` が OSI 承認済みの SDPX 3.10 識別子のみを含むかどうかを確認します。

!!! warning
    [`licensecheck`](@ref) は SDPX 3.10 よりも多くのライセンスを理解し、SDPX 3.10 識別子ではない結果を出力することがあります。そのようなライセンスは、OSI の地位に関係なく `is_osi_approved(name) == false` を返します。


## 例

```julia
julia> is_osi_approved("MIT")
true

julia> is_osi_approved(find_license(pkgdir(LicenseCheck)))
true

julia> is_osi_approved(find_license(homedir(), allow_brute=false)) # ライセンスはありません
false

```
