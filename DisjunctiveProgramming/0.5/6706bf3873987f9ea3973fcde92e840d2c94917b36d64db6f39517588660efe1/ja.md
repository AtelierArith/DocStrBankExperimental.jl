```
GDPModel([optimizer]; [kwargs...])::JuMP.Model

GDPModel{T}([optimizer]; [kwargs...])::JuMP.GenericModel{T}

GDPModel{M <: JuMP.AbstractModel, VrefType, CrefType}([optimizer], [args...]; [kwargs...])::M
```

一般的な選択プログラミングモデルを構築するためのコアモデルオブジェクトです。
