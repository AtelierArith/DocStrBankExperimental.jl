```
on(f, c::Camera, observables::Observable...)
```

カメラのオブザーバブルをマッピングする際、後でカメラのステアリング信号を切断しやすくするために、それらを `steering_node` ベクターに格納します！
