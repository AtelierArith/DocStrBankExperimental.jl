```
AtariEnv(name; colorspace = "Grayscale", frame_skip = 4, noopmax = 20,
               color_averaging = true, repeat_action_probability = 0.)
```

RLSetupの[ReinforcementLearning](https://github.com/jbrea/ReinforcementLearning.jl)パッケージで使用できるAtariEnvを返します。利用可能な`name`をすべて確認するには、ArcadeLearningEnvironmentパッケージのdeps/romsフォルダーをチェックしてください。
