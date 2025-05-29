```
ensure_artifact_installed(name::String, artifacts_toml::String;
                          platform::AbstractPlatform = HostPlatform(),
                          pkg_uuid::Union{Base.UUID,Nothing}=nothing,
                          verbose::Bool = false,
                          quiet_download::Bool = false,
                          io::IO=stderr)
```

アーティファクトがインストールされていることを確認し、必要に応じて`artifacts_toml`に保存されたダウンロード情報を介してダウンロードします。 インストールできない場合はエラーをスローします。
