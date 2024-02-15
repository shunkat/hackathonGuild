This is a Kotlin Multiplatform project targeting Android, iOS, Web, Desktop, Server.

* `/composeApp` is for code that will be shared across your Compose Multiplatform applications.
  It contains several subfolders:
  - `commonMain` is for code that’s common for all targets.
  - Other folders are for Kotlin code that will be compiled for only the platform indicated in the folder name.
    For example, if you want to use Apple’s CoreCrypto for the iOS part of your Kotlin app,
    `iosMain` would be the right folder for such calls.

* `/iosApp` contains iOS applications. Even if you’re sharing your UI with Compose Multiplatform, 
  you need this entry point for your iOS app. This is also where you should add SwiftUI code for your project.

* `/server` is for the Ktor server application.

* `/shared` is for the code that will be shared between all targets in the project.
  The most important subfolder is `commonMain`. If preferred, you can add code to the platform-specific folders here too.


Learn more about [Kotlin Multiplatform](https://www.jetbrains.com/help/kotlin-multiplatform-dev/get-started.html),
[Compose Multiplatform](https://github.com/JetBrains/compose-multiplatform/#compose-multiplatform),
[Kotlin/Wasm](https://kotl.in/wasm/)…

**Note:** Compose/Web is Experimental and may be changed at any time. Use it only for evaluation purposes.
We would appreciate your feedback on Compose/Web and Kotlin/Wasm in the public Slack channel [#compose-web](https://slack-chats.kotlinlang.org/c/compose-web).
If you face any issues, please report them on [GitHub](https://github.com/JetBrains/compose-multiplatform/issues).

You can open the web application by running the `:composeApp:wasmJsBrowserDevelopmentRun` Gradle task.

# memo
## DB設計


### エンティティと属性

1. **ユーザー(User)**
   - UserID (主キー)
   - ユーザー名
   - メールアドレス
   - パスワード (ハッシュ化)
   - その他ユーザー情報 (例: プロフィール情報など)

2. **ハッカソン(Hackathon)**
   - HackathonID (主キー)
   - ハッカソン名
   - 開催日
   - 終了日
   - 詳細説明

3. **チーム(Team)**
   - TeamID (主キー)
   - HackathonID (外部キー)
   - チーム名
   - 説明
   - 募集状況 (募集中、募集終了など)

4. **役割(Role)**
   - RoleID (主キー)
   - 役割名
   - 説明

### 関連テーブル

1. **チーム役割募集(TeamRole)**
   - TeamRoleID (主キー)
   - TeamID (外部キー)
   - RoleID (外部キー)
   - 必要人数
   - 現在の人数

2. **ユーザーチーム参加(UserTeam)**
   - UserTeamID (主キー)
   - UserID (外部キー)
   - TeamID (外部キー)
   - RoleID (外部キー)
   - 参加状況 (例: 確定、申請中など)
