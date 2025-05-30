```
delete!(commp::CommunityProfile, sample::AbstractString, prop::Symbol)
```

`commp`から`sample`のメタデータエントリを`prop`というシンボルを使用して削除します。存在しない場合はエラーをスローします。値が存在しない場合にエラーをスローしたくない場合は、[`unset!`](@ref)を使用してください。
