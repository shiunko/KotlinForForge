# KotlinForForge
Makes Kotlin forge-friendly by doing the following:
- Provides the Kotlin libraries.
- Provides `KotlinLanguageProvider` to allow usage of object declarations as @Mod targets.
- Provides `AutoKotlinEventBusSubscriber` to allow usage of object declarations as @Mod.EventBusSubscriber targets.
- Provides useful utility functions and constants
- Provides its own implementation of the Forge eventbus to work with KCallables and reified type parameters
- Provides sided property delegates and object holder property delegates

An example mod is provided at the [KotlinModdingSkeleton repository](https://github.com/thedarkcolour/KotlinModdingSkeleton).

If you aren't sure where to start, make a fork of the KotlinModdingSkeleton repository.
```git
git clone https://github.com/thedarkcolour/KotlinModdingSkeleton.git
```

To implement in an existing project, paste the following into your build.gradle:
```groovy
buildscript {
    dependencies {
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:1.4.10"
    }
}

apply plugin: 'kotlin'

repositories {
    maven {
        name = 'kotlinforforge'
        url = 'https://thedarkcolour.github.io/KotlinForForge/'
    }
}

dependencies {
    // Use the latest version of KotlinForForge
    implementation 'thedarkcolour:kotlinforforge:1.7.0'
}

compileKotlin {
    kotlinOptions {
        jvmTarget = '1.8'
    }
}
```
Then, change the following to your mods.toml file:
```toml
modLoader="kotlinforforge"
# Change this if you require a certain version of KotlinForForge
loaderVersion="[1,)"
```

Use
```thedarkcolour.kotlinforforge.forge.MOD_CONTEXT```              
instead of ```net.minecraftforge.fml.javafmlmod.FMLJavaModLoadingContext```
