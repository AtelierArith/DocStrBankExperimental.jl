```
f = get_inb(pedlist [,check, sorthere, method])
f = get_inb(s, d [,check, sorthere, method])
f = get_inb(Tv, pedlist [,check, sorthere, method])
```

系譜リスト `pedlist` における動物の近親交配係数を計算します。このリストは整数行列（2 x *n*、ここで *n* は動物の数）です。また、父親と母親のリスト（それぞれ `s` と `d`）を提供することもできます。結果はベクトル `f` に格納され、型は `Tv`（デフォルトは Float64）です。未知の親グループ（UPG）は欠損コード（`0`）で置き換えられます。

系譜は親がその子孫に先行するようにコーディングされるべきです。すべての子孫はその先祖よりも大きなコードを持たなければなりません。デフォルトでは、関数は系譜が「順列」されているかどうかをチェックし、間違っている場合は停止します。チェックを省略するには `check=false` を指定します。この関数内で系譜を時間的に順序付けたい場合は、`sorthere=true` を指定してください。

デフォルトの方法は Meuwissen と Luo (1992) です。このバージョンでサポートされている唯一の方法です。

### 例

```jldoctest
julia> using PedigreeTools;

julia> pedlist,idtable = read_ped("pedigree.txt");

# 動物が時間的にソートされていると仮定します。
julia> f = get_inb(pedlist);

# ここで動物をソートします。
julia> f = get_inb(pedlist, sorthere=true);
```
