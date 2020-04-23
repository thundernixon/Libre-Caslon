# Finishing the VF upgrade project

This variable font upgrade was started in Q4 2018, and now it is Q2 2020. Largely, this is because I was working on other projects, especially Recursive Mono & Sans. Partially, this delay was due to the font previously having Regular–Bold Romans, but only a Regular Italic (but no a Bold Italic), making it a "non-rectangular" family. Recently, however, @KatjaSchimmel has drawn a Bold Italic and greatly improved the spacing of the Regular Italic. So, it's back to mastering!

## Build

I've added a fontmake line for `sources/LibreCaslonText-Italic.glyphs` to `build.sh`, and after fixing an errant point in the glyph `Z` plus copying arrows from the Regular to the 

![roman & italic variable font build](vf-build.gif)

## Fixing

### Ligature Carets

Earlier, I had added ligature carets, but then turned them off by changing their names.

So, I changed their names back with the following macro:

```
font = Glyphs.font

def fixCarets(layer):
    for anchor in layer.anchors:
        anchor.name = anchor.name.replace("lig_","").replace("carrot","caret").replace("_temp_off","")


for glyph in font.glyphs:
    if "_" in glyph.name:
        print(glyph.name)
        for layer in glyph.layers:
            print("    ", layer.name)
        	fixCarets(layer)
```