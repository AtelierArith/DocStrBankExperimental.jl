```
init( julianparseddict::Dict)
```

Initialize if the sdk key is in Julian dict format and the file is saved as adminsdkkey.json

## Example

```md julia> r = HTTP.get(BASE_URL, header); # returns a response with header and body HTTP.Messages.Response

julia> response = JSON.parse(String(r.body)) Dict{String, Any} with 10 entries:   "client*email"                => "****"   "client*id"                   => "****"   "auth*uri"                    => "https://accounts.google.com/o/oauth2/auth"   "auth*provider*x509*cert*url" => "https://www.googleapis.com/oauth2/v1/certs"   "token*uri"                   => "https://oauth2.googleapis.com/token"   "client*x509*cert*url"        => "https://www.googleapis.com/robot/v1/metadata/x509/firebase-adminsdk-jk50g%40volka-bot.iam.gserviceaccount.com"   "project*id"                  => "****"   "type"                        => "service*account"   "private*key"                 => "****"   "private*key*id"              => "****"

julia> init(response) Project Admin SDK key is adminsdkkey.json now!! project*id: **** client*email: **** ````
