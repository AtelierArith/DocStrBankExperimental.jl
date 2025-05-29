```
getthumblink(client::PCloudClient; kwargs...)
```

Get a link to a thumbnail of a file

Takes `fileid` (or `path`) as parameter and provides links from which a thumbnail of the file can be downloaded.

Thumbnails can be created only from files whose metadata has `thumb` value set to `true`.

The parameter `size` MUST be provided, in the format WIDTHxHEIGHT.

The width MUST be between 16 and 2048, and divisible by either 4 or 5.

The height MUST be between 16 and 1024, and divisible by either 4 or 5.

By default the thumb will have the same aspect ratio as the original image, so the resulting thumbnail width or height (but not both) might be less than requested.

If you want thumbnail exactly the size specified, you can set `crop` parameter. With `crop`, thumbnails will still have the right aspect ratio, but if needed some rows or cols (but not both) will be cropped from both sides. So if you have 1024x768 image and are trying to create 128x128 thumbnail, first the image will be converted to 768x768 by cutting 128 columns from both sides and then resized to 128x128. To create a rectangular thumb from 4:3 image exactly 1/8 is cropped from each side. By default the thumbnail is in jpeg format.

If the `type` parameter is set to png, a png image will be produced.

Thumbs are created on first request and cached for unspecified amount of time (or until file) changes.

Clients should attempt to cache thumbs if space permits.

It is also advisable to monitor the original file's `hash` to see if it has changed. If yes, a new thumbnail MUST be requested.

Source: https://docs.pcloud.com/methods/thumbnails/getthumblink.html

# Arguments

  * `fileid::Int`: id of the file for thumb
  * `path::String`: filepath to the file for thumb
  * `size::String`: WIDTHxHEIGHT

Use `fileid` or `path`

# Optional Arguments

  * `crop::Int`: If set, then the thumb will be cropped
  * `type::String`: If set to png, then the thumb will be in png format

# Output

On success the same data as with `getfilelink` is returned.

Additionally the real image produced `size` is returned

It will match reqested size if `crop` is specified or may differ otherwise.

# Output Example

```
{
    result: 0,
    size: "32x32",
    path: "/hash/My%20thumb.jpg",
    expires: "Thu, 03 Oct 2013 01:06:49 +0000",
    hosts: [
        "c63.pcloud.com",
        "c1.pcloud.com"
    ]
}
```
