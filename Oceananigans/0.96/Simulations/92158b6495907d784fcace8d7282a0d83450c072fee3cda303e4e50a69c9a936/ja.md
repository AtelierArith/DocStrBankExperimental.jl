```
conjure_time_step_wizard!(simulation, schedule=IterationInterval(5), wizard_kw...)
```

`wizard_kw`を使用して構築された`TimeStepWizard`を`Callback`として`simulation`に追加し、デフォルトで`IterationInterval(5)`である`schedule`で呼び出します。
