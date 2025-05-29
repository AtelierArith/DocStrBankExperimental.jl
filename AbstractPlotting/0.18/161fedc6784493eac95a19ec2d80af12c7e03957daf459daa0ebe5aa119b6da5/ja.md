```
rotate_cam!(scene::Scene, theta_v::Number...)
rotate_cam!(scene::Scene, theta_v::VecTypes)
```

シーンのカメラを指定された回転で回転させます。`theta_v = (α, β, γ)`を渡すと、カメラはオイラー角(α, β, γ)に従って回転します。
