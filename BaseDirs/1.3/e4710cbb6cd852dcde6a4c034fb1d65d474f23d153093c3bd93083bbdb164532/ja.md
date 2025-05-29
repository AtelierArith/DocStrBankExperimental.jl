**BaseDirs.User**

このモジュールは、ユーザー固有のディレクトリへのアクセサ関数を含んでいます。

### ベースディレクトリアクセサ

関数 [`data`](@ref BaseDirs.User.data)、[`config`](@ref BaseDirs.User.config)、[`state`](@ref BaseDirs.User.state)、[`cache`](@ref BaseDirs.User.cache)、および [`runtime`](@ref BaseDirs.User.runtime) は `String` を生成します。

### ユーザーディレクトリアクセサ

関数 [`desktop`](@ref BaseDirs.User.desktop)、[`downloads`](@ref BaseDirs.User.downloads)、[`music`](@ref BaseDirs.User.music)、[`videos`](@ref BaseDirs.User.videos)、[`templates`](@ref BaseDirs.User.templates)、[`public`](@ref BaseDirs.User.public) は `String` を生成します。

### その他のアクセサ

関数 [`fonts`](@ref BaseDirs.User.fonts) と [`applications`](@ref BaseDirs.User.applications) は `Vector{String}` を生成します。

!!! note
    [`System`](@ref BaseDirs.System) および "combined" (`BaseDirs.*`) アクセサとは異なり、ここでの *Base* および *User* アクセサは単一のディレクトリ (`String`) を返します。

