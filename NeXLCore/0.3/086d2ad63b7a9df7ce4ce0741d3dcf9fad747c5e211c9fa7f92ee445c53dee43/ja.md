```
loadcustommac!(elm::Element, cxr::CharXRay, source::AbstractString)
```

指定された `CharXRay` に関連付けられたカスタム質量吸収係数を `Element` からソースにロードします。利用可能な MAC を探るには `listcustommacs(cxr)` を使用してください。
