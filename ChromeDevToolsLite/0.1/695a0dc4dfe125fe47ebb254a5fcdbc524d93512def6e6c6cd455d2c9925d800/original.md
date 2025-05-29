```
goto(page::Page, url::String; verbose::Bool=false)
```

Navigate to the specified URL and wait for page load.

# Arguments

  * `page::Page`: The page to navigate
  * `url::String`: The URL to navigate to
  * `verbose::Bool`: Enable verbose logging (default: false)

# Throws

  * `NavigationError`: If navigation fails or times out
