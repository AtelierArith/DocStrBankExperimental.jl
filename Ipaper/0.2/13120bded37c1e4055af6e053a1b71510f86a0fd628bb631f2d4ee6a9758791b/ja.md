```
aria2c(infile, args="";
    j=5, s=5, x=5, outdir=".",
    verbose=false, debug=false, run=true)
```

# インストール

  * `windows`: `scoop install aria2`
  * `linux`: `sudo apt install aria2`

# 引数

  * `j`: `--max-concurrent-downloads=N` 各静的 (HTTP/FTP) URL、トレント、およびメタリンクのための最大同時ダウンロード数を設定します。 –split および –optimize-concurrent-downloads オプションも参照してください。 可能な値: 1-*, デフォルト: 5, タグ: #basic
  * `s`: `--split=N` N 接続を使用してファイルをダウンロードします。 N より多くの URI が指定された場合、最初の N URI が使用され、残りの URL はバックアップ用に使用されます。 N より少ない URI が指定された場合、それらの URL は N 接続が同時に行われるように複数回使用されます。同じホストへの接続数は –max-connection-per-server オプションによって制限されます。 –min-split-size オプションも参照してください。 可能な値: 1-*, デフォルト: 5, タグ: #basic, #http, #ftp
  * `x`: –max-connection-per-server=NUM 各ダウンロードのための1つのサーバーへの最大接続数。 可能な値: 1-16, デフォルト: 1, タグ: #basic, #http, #ftp
  * `timeout`: 秒単位、デフォルト 10s。 aria2c ではデフォルトで `timeout=120s` であることに注意してください。

# 例

```julia
using Ipaper
using NetCDFTools.CMIP

infile = "/mnt/z/CMIP6/CMIP6_global_WB/urls.txt"
outdir = "/mnt/z/CMIP6/CMIP6_global_WB/raw"

@time f_rem = aria2c_rem(infile; outdir)

# hostS_bad = []
hosts_bad = ["esg-dn1.nsc.liu.se", "esg-dn2.nsc.liu.se", "esgf.bsc.es"]
f_left = aria2c(f_rem; outdir, check_rem=false, run=false, hosts_bad, timeout=10)
kill_app()

urls = readlines(f_rem)
hosts = get_host.(urls)
table(hosts)

info = CMIPFiles_info(urls)
s = CMIPFiles_summary(info)
```
