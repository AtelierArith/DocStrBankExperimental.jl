```
transitionfrequency(ion, transition::Tuple, chamber::Chamber; ignore_manualshift=false)
```

返すのは、`T`内の位置に基づいて`ion`が経験するゼーマンシフトを含む遷移`transition`の周波数です。`ion`は、`chamber`内の希望するイオンのインデックスを示すIonまたはIntのいずれかです。
