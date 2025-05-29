```
prettylens(lens::Lens; sprint_kwargs...) :: String
prettylens(io::IO, lens::Lens)
```

`lens`のよりコンパクトで読みやすい文字列表現を`show`よりも印刷または返します。

# 例

```jldoctest
julia> using Setfield, Kaleido

julia> prettylens(
           (@lens _.a) ∘ MultiLens((
               (@lens last(_)),
               (@lens _[:c].d) ∘ settingasℝ₊,
           ));
           context = :compact => true,
       )
"◻.a∘〈last(◻),◻[:c].d∘(←exp|log→)〉"
```
