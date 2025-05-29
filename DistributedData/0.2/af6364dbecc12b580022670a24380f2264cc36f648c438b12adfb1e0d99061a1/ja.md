```
function dselect(dInfo::Dinfo,
    currentColnames::Vector{String}, selectColnames::Vector{String};
    tgt=dInfo.val)::Dinfo
```

列名で動作する `dselect` の便利なオーバーロードです。
