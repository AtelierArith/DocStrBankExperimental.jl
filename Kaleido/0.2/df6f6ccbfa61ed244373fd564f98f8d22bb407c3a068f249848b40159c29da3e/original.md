```
prettylens(lens::Lens; sprint_kwargs...) :: String
prettylens(io::IO, lens::Lens)
```

Print or return more compact and easier-to-read string representation of `lens` than `show`.

# Examples

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
