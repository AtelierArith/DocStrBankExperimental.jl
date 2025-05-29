```
init!(tracker::Tracker, x₁, t₁, t₀)
```

`tracker`を`t₁`から`t₀`まで`x₁`を追跡するように設定します。

```
init!(tracker::Tracker, t₀)
```

`tracker`を現在の解を`t₀`まで追跡し続けるように設定します。これにより、現在の状態が保持されます。
