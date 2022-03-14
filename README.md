# tv.unbuffer.com repo

AppleTV targeted repo for [unbuffer blog](https://unbuffer.com)

All packages property of their authors. I offer my thanks and don't claim ownership of anything unless stated. Please support the package authors and don't use the packages for piracy or other illegal/imoral activity.

The packages are hosted here to help me perform application security testing on my devices, though you are probably free to use them under their respective licenses where laws permit.

No warranty or support offered. These packages could possibly break your device / cost you time or money / wreck or lead your data and many other things.

USE AT YOUR OWN RISK!


# Based on Reposi3

https://github.com/supermamon/Reposi3/

A Cydia repository template. This template contains sample on how you can easily make depiction pages without replicating your html pages. The pages are styled using [Bootstrap](http://getbootstrap.com/) which is really easy to use. You can see how it looks like by visiting [this sample repo](https://supermamon.github.io/Reposi3/) on your desktop or mobile phone.

# Adding packages to repo

#### 1. Adding a simple depiction page

Go to the depictions folder and duplicate the folder `com.supermamon.oldpackage`.
Rename the duplicate with the same name as your package name.
There are 2 files inside the folder - `info.xml` and `changelog.xml`.
Update the 2 files with information regading your package.
The tags are pretty much self-explanatory.
Contact [@reposi3](https://twitter.com/reposi3) for questions.

`info.xml`.
```xml
<package>
    <id>com.supermamon.oldpackage</id>
    <name>Old Package</name>
    <version>1.0.0-1</version>
    <compatibility>
        <firmware>
            <miniOS>5.0</miniOS>
            <maxiOS>7.0</maxiOS>
            <otherVersions>unsupported</otherVersions>
            <!--
            for otherVersions, you can put either unsupported or unconfirmed
            -->
        </firmware>
    </compatibility>
    <dependencies></dependencies>
    <descriptionlist>
        <description>This is an old package. Requires iOS 7 and below..</description>
    </descriptionlist>
    <screenshots></screenshots>
    <changelog>
        <change>Initial release</change>
    </changelog>
    <links></links>
</package>
```

`changelog.xml`.
```xml
<changelog>
    <changes>
        <version>1.0.0-1</version>
        <change>Initial release</change>
    </changes>
</changelog>
```


#### 2. Link the depiction page your tweak's `control` file

For the depictions to appear on Cydia, you will need to add the depictions url at the end of your package's `control` file before compiling it.
The control file should look like this:

```text
Package: com.supermamon.oldpackage
Name: Old Package
Section: Tweaks
Depends: firmware (<7.0)
Description: This is a sample old package. Firmware should be lower than 7.0
Depiction: https://username.github.io/repo/depictions/?p=[idhere]
```

Replace `[idhere]` with your actual package name.

```text
Depiction: https://username.github.io/repo/depictions/?p=com.supermamon.oldpackage
```

#### 3. Rebuilding the `Packages` file

With your updated `control` file, build your tweak.
Store the resulting `.deb.` file into the `/debs/` folder of your repo.
Build your `Packages` file and compress with `bzip2`.

```sh
user:~/ $ cd repo
user:~/repo $ dpkg-scanpackages -m ./debs > Packages
user:~/repo $ bzip2 Packages
```

_Windows users, see [dpkg-scanpackages-py](https://github.com/supermamon/dpkg-scanpackages-py) or [scanpkg](https://github.com/mstg/scanpkg)._

#### 5. Cydia at last!

Push your changes again to Github and if you haven't done yet, go ahead and add your repo to Cydia.
You should now be able to install your tweak into your own repo.

### Cleanup

Just a cleanup step, remove the debs that came with this template and re-run the commands on step 3. You can keep the sample depictions for reference by they're not needed for your repo.
