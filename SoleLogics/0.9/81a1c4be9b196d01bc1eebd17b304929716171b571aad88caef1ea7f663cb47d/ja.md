```
struct KripkeStructure{
    FR<:AbstractFrame,
    MAS<:AbstractDict
} <: AbstractKripkeStructure
    frame::FR
    assignment::AS
end
```

[Kripke structures](https://en.wikipedia.org/wiki/Kripke_structure_(model_checking))を明示的に表現するための型; それは`frame`と、各世界に解釈を割り当てる抽象辞書をラップします。
