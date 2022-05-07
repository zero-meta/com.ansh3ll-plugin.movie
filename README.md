# Movie
Easy video playback on the OpenGL display hierarchy. Supports `Ogg Theora` videos

More info on this plugin can be found [here](https://github.com/ANSH3LL/plugin_movie)

# Integration
Add the plugin to your build settings like so:
```lua
plugins = {
    ["plugin.movie"] = {
        publisherId = "com.ansh3ll"
    },
},
```

Simple usage example like so:
```lua
local movie = require('plugin.movie')

local function movieListener(event)
    if event.phase == 'stopped' then
        print('Video watched to end? ', event.completed)
    end
    --
    for k, v in pairs(event) do
        print(k .. ' = ' .. v)
    end
end

local player = movie.newMovieRect(
    {
        x = display.contentCenterX,
        y = display.contentCenterY,
        width = 960,
        height = 540,
        channel = 3,
        listener = movieListener,
        filename = 'intro_cutscene.ogv'
    }
)

audio.setVolume(1, {channel = player.channel})
player.play()
```

A more advanced usage example can be found [here](https://github.com/ANSH3LL/plugin_movie/tree/main/Corona)

# Credits
- [theoraplay](https://github.com/icculus/theoraplay) by [@icculus](https://github.com/icculus)
- Insipired by the [theora](https://github.com/ggcrunchy/solar2d-plugins/tree/master/theora) plugin by [@ggcrunchy](https://github.com/ggcrunchy) as well as a video wrapper provided by a user of the [Solar2D discord](https://discord.gg/WMtCemc)
- macOS and iOS builds by [@kwiksher](https://github.com/kwiksher)
