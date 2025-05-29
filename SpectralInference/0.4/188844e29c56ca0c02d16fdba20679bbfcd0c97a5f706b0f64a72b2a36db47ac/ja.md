```
projectout(usv::SVD, [window])
```

は元の行列を再作成します。すなわち、$UΣV'$ を計算するか、ウィンドウが含まれている場合は、提供されたコンポーネントに基づいて元の行列のスペクトルフィルタリングされたバージョンを作成します。

すなわち、`usv.U[:, window] * diagm(usv.S[window]) * usv.Vt[window, :]`
