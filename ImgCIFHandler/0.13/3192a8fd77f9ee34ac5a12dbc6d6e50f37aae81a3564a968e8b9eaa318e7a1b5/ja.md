```
peak_to_frames(p::Peak, cc::CifContainer;single=false, friedel=true)
```

ピーク `p` を考慮して、ピクセルが表示されるべきピークの配列を返します。もし同じスキャンからのピークのみをチェックする必要がある場合は、`single` を true に設定してください。
