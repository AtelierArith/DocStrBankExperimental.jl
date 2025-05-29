プロフィールの更新 ユーザーのプロフィール（表示名 / 写真のURL）を更新するには、AuthのsetAccountInfoエンドポイントにHTTP POSTリクエストを送信します。

# TODO: 属性の削除

# 例

`julia data = firebase_signin("ab669522@gmail.com","helloworld!!") firebase_updateprofile("ash","https://i.imgur.com/zgDkgSR.jpeg",data["idToken"]) #=        Dict{String, Any} with 8 entries:   "kind"             => "identitytoolkit#SetAccountInfoResponse"   "photoUrl"         => "https://i.imgur.com/zgDkgSR.jpeg"   "localId"          => "GovyExPqFWS70uynnuBzVnYgLAi2"   "displayName"      => "ash"   "passwordHash"     => "UkVEQUNURUQ="   "emailVerified"    => false   "providerUserInfo" => Any[Dict{String, Any}("rawId"=>"ab669522@gmail.com", "photoUrl"=>"https:…   "email"            => "ab669522@gmail.com" =#`
