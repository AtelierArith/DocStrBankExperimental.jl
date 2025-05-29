```
export_static(html_file::Union{IO, String}, app::App)
export_static(folder::String, routes::Routes)
```

Exports the app defined by `app` with all its assets a single HTML file. Or exports all routes defined by `routes` to `folder`.
