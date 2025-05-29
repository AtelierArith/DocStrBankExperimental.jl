```
TwistedBoundary <: Boundary
```

位相ツイストを持つ境界条件。`PeriodicBoundary`は、ツイストがゼロの`TwistedBoundary`の特別なケースです。

---

```
TwistedBoundary(translation, Θ)
```

与えられた変換とツイスト角度で`TwistedBoundary`を構築します。

## 引数

  * `translation`: `AbstractTranslation`として表される境界の変換ベクトル。配列が渡されると、自動的に`Translation`に変換されます。
  * `Θ`: ラジアンでのツイスト角度。
