```julia
function studentTest1S!(y::UniData; <same args and kwargs as `studentTest1S`>)
```

[`studentTest1S`](@ref) と同様ですが、近似（ランダム置換）テストの場合は `y` が上書きされます。

**エイリアス:** `tTest1S!`

**多重比較バージョン:** [`studentMcTest1S!`](@ref)
