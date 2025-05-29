```
Body{T} <: Node{T}

剛体オブジェクト

id: 一意の識別番号 
name: 一意の識別名 
mass: 慣性特性 (キログラム)
inertia: 慣性行列 (キログラム メートル^2)
state: State; システムの位置、線形速度、向き、および角速度の表現 
shape: Shape; Bodyに関する幾何情報
```
