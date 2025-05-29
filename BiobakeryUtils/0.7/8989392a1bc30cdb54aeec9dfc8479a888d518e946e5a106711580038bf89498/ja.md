```
function humann_regroup(comm::CommunityProfile; inkind="uniref90", outkind::String="ec")
```

`humann_regroup_table` スクリプトのラッパーで、ある種類の機能マッピングから別の種類にテーブルを変換します。

`ENV["PATH"]` で利用可能な [`humann`](https://github.com/biobakery/humann) のインストールが必要です。詳細については "[Using Conda](@ref using-conda)" を参照してください。
