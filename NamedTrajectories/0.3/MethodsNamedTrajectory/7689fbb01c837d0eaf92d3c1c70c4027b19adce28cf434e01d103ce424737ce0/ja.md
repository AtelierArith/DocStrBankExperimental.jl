```
add_component!(traj, name::Symbol, data::AbstractVecOrMat; type={:state, :control, :slack})
```

軌道にコンポーネントを追加します。

この関数は軌道のサイズを変更するため、グローバルコンポーネントとコンポーネントを調整する必要があります。
