get_request(url::String)

# Get request which is general in nature and gets any document or collection

# Example

```julia
init("[FIREBASE_ADMIN_SDK].json")
res = get_request("/firebase_test/firebase_get") # document get
res = get_request("/firebase_test/firebase_get/firebase_get_collection") # collection fetch
```
