```
aria2c(infile, args="";
    j=5, s=5, x=5, outdir=".",
    verbose=false, debug=false, run=true)
```

# Installation

  * `windows`: `scoop install aria2`
  * `linux`: `sudo apt install aria2`

# Arguments

  * `j`: `--max-concurrent-downloads=N` Set maximum number of parallel downloads for

every static (HTTP/FTP) URL, torrent and metalink.  See also –split and –optimize-concurrent-downloads options.  Possible Values: 1-*, Default: 5, Tags: #basic

  * `s`: `--split=N` Download a file using N connections. If more than N URIs

are given, first N URIs are used and remaining URLs are used for backup.  If less than N URIs are given, those URLs are used more than once so that  N connections total are made simultaneously. The number of connections to the  same host is restricted by the –max-connection-per-server option. See also the  –min-split-size option.  Possible Values: 1-*, Default: 5, Tags: #basic, #http, #ftp

  * `x`: –max-connection-per-server=NUM The maximum number of connections to one

server for each download.  Possible Values: 1-16, Default: 1, Tags: #basic, #http, #ftp

  * `timeout`: in seconds, default 10s. Notice that `timeout=120s` in aria2c by default.

# Examples

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
