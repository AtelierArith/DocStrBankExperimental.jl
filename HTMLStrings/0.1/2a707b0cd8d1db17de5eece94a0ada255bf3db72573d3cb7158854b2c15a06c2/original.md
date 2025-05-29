```
tag(tag_name, args...)
```

Generate an HTML tag with the given `tag_name` and attributes/content/nested tags specified in `args`.

## Examples

### Basic Usage

```julia
# Generate an <h1> tag with content
println(tag("h1", "Hello, World!"))  
# Output: "<h1>Hello, World!</h1>"

# Generate a <p> tag with a class attribute and content
println(tag("p", :class => "text-lg", "This is a paragraph."))  
# Output: "<p class="text-lg">This is a paragraph.</p>"
```

### Nested Tags

```julia
# Generate a <div> with nested <p> and <span> tags
println(tag("div", tag("p", "A paragraph."), tag("span", "A span.")))  
# Output: "<div><p>A paragraph.</p><span>A span.</span></div>"
```

### Special Attributes

```julia
# Generate a <var> tag with a custom attribute
println(tag("var", :data_value => "42", "x"))  
# Output: "<var data-value="42">x</var>"
```

### Mixing Attributes, Content, and Nested Tags

```julia
# Generate an <a> tag with a href attribute, class attribute, and content
println(tag("a", :href => "https://example.com", :class => "link", "Visit Example"))  
# Output: "<a href="https://example.com" class="link">Visit Example</a>"
```

## Notes

  * `tag_name` should be a string representing the HTML tag name (e.g., "div", "span", "h1").
  * `args` can be a mix of:
  * Pairs for attributes (e.g., `:class => "text-lg"`)
  * Strings for content (e.g., `"Hello, World!"`)
  * Functions for nested tags (e.g., `tag("p", "A paragraph.")`)
