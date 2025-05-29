```
ContactConstraint{T} <: Constraint{T}

接触ノードに関する情報を含む制約。

id: 一意の識別番号 
name: 一意の識別名 
model: 接触モデルのタイプ: ImpactContact, LinearContact, NonlinearContact 
parent_id: 接触を経験しているBodyの識別番号 
child_id: 常に0
impulses: Bodyに適用される接触インパルス 
impulses_dual: 正しい接触挙動を強制するためにソルバーによって使用される双対接触インパルス
```
