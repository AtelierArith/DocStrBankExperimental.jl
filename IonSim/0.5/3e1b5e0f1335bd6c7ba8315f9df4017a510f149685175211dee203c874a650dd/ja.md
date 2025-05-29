```
ionstate(object::Union{IonTrap, Chamber}, sublevels)
```

もし `N = length(ions(object))` の場合、N次元のケトが返され、これはイオンが状態 $|sublevel₁⟩⊗|sublevel₂⟩⊗...⊗|sublevel\_N⟩$ にあることを示します。

`sublevels` は長さ `N` のベクトルでなければならず、各要素は対応するイオンのサブレベルを指定します。これは `ionstate(ion::Ion, sublevel)` と同じ構文を使用します。
