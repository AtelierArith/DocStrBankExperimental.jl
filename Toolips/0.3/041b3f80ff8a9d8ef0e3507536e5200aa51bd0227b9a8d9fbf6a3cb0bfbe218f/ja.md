#### toolips 0.3 - マニックなウェブ開発フレームワーク

  * 2024年1月に [chifi](https://github.com/orgs/ChifiSource) によって作成されました。
  * このソフトウェアはMITライセンスです。

Toolipsは、Juliaプログラミング言語のための**拡張可能**、*宣言的*、および**多用途**のウェブ開発フレームワークです。

```example
module MyServer
using Toolips
using Toolips.Components
# import 
# create a logger
logger = Logger()

# quick extension

const people = Extension{:people}

# mount directory "MyServer/public" to "/public"
public = mount("/public" => "public")

# create a route
main = route("/") do c::Connection

end

# export routes
export public
export main

# export extensions
export logger
end # module
```

##### 提供するもの

  * `new_app`
  * `default_404`
  * `Components`
  * `make_docroute`
  * **core**

      * `Cookie` (see `respond!`)
      * `IP4`
      * `get(::String)`
      * `post`
      * `AbstractConnection`
      * `distribute!`
      * `assign!`
      * `assign_open!`
      * `distribute_open!`
      * `waitfor`
      * `put!`
      * `Connection`
      * `write!`
      * `IOConnection`
      * `get_ip`
      * `get_ip4`
      * `get_args`
      * `get_post`
      * `get_method`
      * `get_route`
      * `get_host`
      * `get_client_system`
      * `get_heading`
      * `get_headers`
      * `get_parent`
      * `get_cookies`
      * `download!`
      * `proxy_pass!`
      * `respond!`
      * `Route`
      * `route`
      * `route!`
      * `AbstractExtension`
      * `QuickExtension`
      * `on_start`
      * `ServerTemplate`
      * `WebServer`
      * `kill!`
      * `start!`
      * `connect`
  * **extensions**

      * `MobileConnection`
      * `Logger`
      * `log(::AbstractConnection, ::String, ::Int64)`
      * `mount`
