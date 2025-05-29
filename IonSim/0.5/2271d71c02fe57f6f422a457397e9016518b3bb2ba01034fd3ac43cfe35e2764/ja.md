```
LinearChain_fromyaml(ions::Vector{<:Ion}, yaml::String; N::Int=10)
```

指定された `yaml` ファイルから通常モード構造をロードします。物理性を強制するのはユーザーの責任です。

```
x:
  - frequency: 1e6
    mode: [0.1, 0.5, 0.3, 0.8]
  - frequency: 2e6
    mode: [0.3, 0.6, 0.5, 3]
y:
  - frequency: 8e6
    mode: [1, 1, 1, 1]
ionpositions: [-1, -0.5, -0.25, 5]
```

この構造の物理性を強制するのはユーザーの責任です。
