# myMetalTestRayBreak

[Beginning Metal](https://www.raywenderlich.com/3537-beginning-metal/lessons/1) を参考にPythonista3 でMetal をしている時に、log 確認用で実行をしているが、Part9 くらいからXcode でエラーが出ているので、Xcode(Swift) 理解用に実際に操作をしてみる


Pythonista3 でのMetal の[Repository](https://github.com/pome-ta/pystaMetalStudy)


## タグ管理

最初のSample は、[5 - Shaders](https://www.raywenderlich.com/3537-beginning-metal/lessons/5) から始めている

Final やChallenge を完了するたびに、tag を増やしていく想定

## branch 管理

tag だけだと、モバイル(iPhone) の確認が面倒そうなので、branch も切ることにしたいけど

結局Git 操作がよくわかってないのよね


## コード修正

※ 設定情報を書き写したいけど今度

### 6

`Texturable.swift`

``` .swift
extension Texturable {
    func setTexture(device: MTLDevice, imageName: String) -> MTLTexture? {
        let textureLoader = MTKTextureLoader(device: device)
        var texture: MTLTexture? = nil
        let origin = NSString(string: MTKTextureLoader.Origin.bottomLeft.rawValue)
        let textureLoaderOptions = [MTKTextureLoader.Option.origin : origin]
        //    let textureLoaderOptions: [String: NSObject]
        //    if #available(iOS 10.0, *) {
        //      let origin = NSString(string: MTKTextureLoaderOriginBottomLeft)
        //      textureLoaderOptions = [MTKTextureLoaderOptionOrigin : origin]
        //    } else {
        //      textureLoaderOptions = [:]
        //    }
        
        if let textureURL = Bundle.main.url(forResource: imageName, withExtension: nil) {
            do {
                texture = try textureLoader.newTexture(URL: textureURL,
                                                       options: textureLoaderOptions)
            } catch {
                print("texture not created")
            }
        }
        return texture
    }
}
```

