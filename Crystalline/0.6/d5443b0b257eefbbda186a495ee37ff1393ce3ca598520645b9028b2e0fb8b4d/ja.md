```
siteirreps(sitegroup::SiteGroup; mulliken::Bool=false]) --> Vector{PGIrrep}
```

提供された `SiteGroup` に関連するサイト対称性の irreps を返します。これは同型点群に対する検索から得られます。`SiteIrrep`s は一般に関連する同型点群の irreps の順列です。

デフォルトでは、サイト対称性の irreps のラベルは CDML 表記で与えられます。マリケン表記を使用するには、キーワード引数 `mulliken` を `true` に設定します（デフォルトは `false` です）。

## 例

```jldoctest
julia> sgnum = 16;

julia> sg = spacegroup(sgnum, 2);

julia> wp = wyckoffs(sgnum, 2)[3] # 3 番目のワイコフ位置を選択
2b: [1/3, 2/3]

julia> siteg = sitegroup(sg, wp)
SiteGroup{2} ⋕16 (p6) at 2b = [1/3, 2/3] with 3 operations:
 1
 {3⁺|1,1}
 {3⁻|0,1}

julia> siteirs = siteirreps(siteg)
3-element Collection{SiteIrrep{2}} for ⋕16 (p6) at 2b = [1/3, 2/3]:
Γ₁┌        1: 1
  ├ {3⁺|1,1}: 1
  └ {3⁻|0,1}: 1

Γ₂┌        1: 1
  ├ {3⁺|1,1}: exp(0.6667iπ)
  └ {3⁻|0,1}: exp(-0.6667iπ)

Γ₃┌        1: 1
  ├ {3⁺|1,1}: exp(-0.6667iπ)
  └ {3⁻|0,1}: exp(0.6667iπ)
```
