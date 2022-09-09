<h1 align="center">Google Summer of Code 2022 <img src="https://media2.giphy.com/media/KB8MHRUq55wjXVwWyl/source.gif" width="50"></h1>

<p align="center"><i>A full report on Google Summer of Code 2022 @ FOSSology</i></p>
<p align="center"><i>Project: "REST API and UI improvements" </i> </p>

<p align="center">
        <img src="https://media4.giphy.com/media/RbDKaczqWovIugyJmW/giphy.gif?cid=ecf05e473b7q8jrsthrdeqzcg6nn08t7jwnsu7m8xcvuuv6c&rid=giphy.gif" width="200">
</p>

![image](https://user-images.githubusercontent.com/66276301/188962690-5869b53c-99bb-4012-b13f-443832568f7e.png)

## Google Summer of Code 2022 🚩 Report: "REST API and UI improvements" 👨‍💻
<!-- 
![ViewCount](https://views.whatilearened.today/views/github/dushimsam/GSoC-2022.svg)
![GitHub](https://img.shields.io/github/followers/dushimsam?style=social)
![Twitter](https://img.shields.io/twitter/follow/dushimsam?style=social)
![GitHub Stars](https://img.shields.io/github/stars/dushimsam/GSoC-2022?style=social) -->

A brief introduction about myself 

I am **Soham Banerjee**, a Computer Science and engineering student at RCCIIT Kolkata. I have been a frontend developer and have been working for many organisations since the past 2 years. Have been an open source software enthusiast since I was introduced to it and, I am grateful to be a part of FOSSology under the GSOC programme 2022.  

In this article I am going to outline the details of my contributions as a reference of project completion during the entire duration of GSOC 2022.


# 🌏 CONTRIBUTIONS 

During this period i have been working on different modules of the project in the three categories:

- **UI IMPROVEMENT:**  Introducing refreshed UI pages in the application with their respective functionalities.

- **EXISITING FEATURE ENHANCEMENT:**  In this category we redefined old features and made them much more usable and user friendly.


- **BUILDING REST APIS:** We introduced many more features using API endpoints so that they can used in the UI

Let's Dive into the processes I implemented during this entire GSOC period. 
## All Recent Jobs Page

_(June 16th, 2022)_

Implementation of the All Recent Jobs page in the UI started.
The response from the `/jobs` endpoint was used in order to get the data from the backend server

Response format of the API: <br/>
![Screenshot from 2022-06-24 10-04-12](/img/reactUI/docs_api_res.png)

At first `MDBReact` datatable was used to render the data but further discussions on optimising the page the idea was scrapped and `X-Total-pages` header was used to get the data from the server in already paginated form.

Final UI of the All Recent jobs page after the discussions looks like: <br/>

![Screenshot from 2022-06-24 10-10-47](/img/reactUI/alljobs_ui_sample.png)

### 👨‍💻 PR link - [feature(ui): /allRecentJobs page completed](https://github.com/fossology/FOSSologyUI/pull/223)

### My Recent Jobs Page

The same API endpoint was used in My Recent Jobs page and the logged in user's UID was fetched from the `getUserSelf()` function.
`MDBReact` table was used here and this requires change to the same UI as of `/allRecentJobs` page.

### 👨‍💻 PR link - [feature(ui): /myRecentJobs page completed](https://github.com/fossology/FOSSologyUI/pull/228)

## Search in Browse Page

There was a search-bar present in the Browse page but, there was no function implented to make the search work. Thus introduced a search function which filters the API response as per the query data and only renders the value which is asked by the user.

### 👨‍💻 PR link - [fix(browse): search bar function implemented ](https://github.com/fossology/FOSSologyUI/pull/230)



![image](https://user-images.githubusercontent.com/66276301/188792421-a50888cf-48e4-46fd-bd4a-8df3bd99127a.png)

**Pull Request** : [feat(UI): Import CSV-license file PAGE](https://github.com/fossology/FOSSologyUI/pull/259)

## Horizontal Pagination implementation

_(June 25th, 2022)_

Implementation of the horizontal page navigator. The pagination module fetches the data from the API on page basis thus reducing the response time of the API.

The All Recent Jobs page with the new Pagination module: <br/>
![pagination](/img/reactUI/pagination.png)

The Module also contains a text box so that user can directly navigate to that particular page at once.
This was suggested by one of the mentors and was implemented after.

### 👨‍💻 PR link - [feat(ui): horizontal pagination added in allRecentJobs](https://github.com/fossology/FOSSologyUI/pull/235)

## /jobs API

Started modifying the /jobs API and currently making a demo docuentation so that the flow of the APIs can be made clear. The API was discussed in the meeting and mentor asked to implement it in a certain suitable way.

Current response of the API: <br/>
![jobs_res](/img/reactUI/jobs_res.png)

Mentors asked to take the user ID as a parameter and not in the URL itself. In addition to this there were suggested changes in the endpoint names and processes which are yet to be implemented.

## Horizontal Pagination implementation in browse page

_(July 3rd, 2022)_

Implementation of the horizontal page navigator in the browse page. The pagination module fetches the data from the API on page basis thus reducing the response time of the API in the browse page. This was implemented earlier in the allRecentJobs page.

The Browse page with the new Pagination module: <br/>
![pagination](/img/reactUI/browse_pagination.png)

### 👨‍💻 PR link - [feat(ui): Pagination in Browse page](https://github.com/fossology/FOSSologyUI/pull/237)

## /jobs API

`/jobs` endpoint now sends only the jobs created by the logged in user. This API can be called by both the Admin and other users.

Fossy user Page: <br/>
![jobs_res](/img/reactUI/fossy_response.png)

Another user's Page: <br/>
![jobs_res](/img/reactUI/buggy_response.png)

Mentors asked to create an flag to get all the jobs irrespective of the user which will only be used by the Admin user.

## Jobs/all endpoint added 

_(July 14th, 2022)_

Implementation of the `jobs/all` API endpoint. this API endpoint sends all the jobs craeted by all the users. This API only sends a response only if the requesting user is an admin.

The API response when the requesting user is an Admin: <br/>
![adimin_res](/img/reactUI/admin_response.png)
<br/>

The API response when the requesting user is Not an Admin: <br/>
![nonAdmin_response](/img/reactUI/nonAdmin_response.png)

### 👨‍💻 PR link - [feat(api): jobs/all endpoint added](https://github.com/fossology/fossology/pull/2260)

## New endpoint for geting copyright details

_(July 21th, 2022)_

Implementation of a new endpoint which gives the copyright information as a response for the requested upload.<br/>
It also provides the respective file paths for each copyright which is reccuring troughout the output.

The API response when requested on a upload (used Nirjas repository here): <br/>

```
[
    {
        "copyright": "Copyright (C) 2020 Ayush Bhardwaj (classicayush@gmail.com), Kaushlendra Pratap (kaushlendrapratap.9837@gmail.com)",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/php.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/c.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/matlab.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/text.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/main.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/scala.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/c_sharp.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/perl.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/java.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/python.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/binder.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/ruby.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/rust.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/javascript.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/kotlin.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/cpp.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/html.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/swift.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/shell.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/css.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/go.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/haskell.py",
            "Nirjas-master.zip/Nirjas-master/setup.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/r.py"
        ]
    },
    {
        "copyright": "Copyright (C) 2020 Siemens AG Author: Gaurav Mishra <mishra.gaurav@siemens.com>",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/nirjas/output/single_line.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/output/__init__.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/output/multi_line.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/output/scan_output.py"
        ]
    },
    {
        "copyright": "Copyright (C) 2020 Aman Dwivedi (aman.dwivedi5@gmail.com)",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/scss.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/typescript.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/tests/test_typescript.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/tests/test_dart.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/tests/test_scss.py",
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/dart.py"
        ]
    },
    {
        "copyright": "Copyright (C) 1991, 1999 Free Software Foundation, Inc. 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA Everyone is permitted to copy and distribute verbatim copies of this license document, but changing it is not allowed.",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "copyright the library, and (2) we offer you this license, which gives you legal permission to copy, distribute and/or modify the library.",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "copyright law: that is to say, a work containing the Library or a portion of it, either verbatim or with modifications and/or translated straightforwardly into another language. (Hereinafter, translation is included without limitation in the term \"modification\".)",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "copyrighted interfaces, the",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "copyrighted by the Free Software Foundation, write to the Free Software Foundation; we sometimes make exceptions for this. Our decision will be guided by the two goals of preserving the free status of all derivatives of our free software and of promoting the sharing and reuse of software generally.",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "copyright\" line and a pointer to where the full notice is found.",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "Copyright (C) <year> <name of author>",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "copyright disclaimer\" for the library, if necessary. Here is a sample; alter the names:",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "copyright interest in the library `Frob' (a library for tweaking knobs) written by James Random Hacker.",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/LICENSE"
        ]
    },
    {
        "copyright": "Copyright (C) 2021 Hamed Faramarzi Author: Hamed Faramarzi <hamed.faramarzi@gmail.com>",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/nirjas/output/output.py"
        ]
    },
    {
        "copyright": "Copyright (C) Sushant Kumar (sushantmishra02102002@gmail.com) SPDX-License-Identifier: LGPL-2.1 This library is free software; you can redistribute it and/or modify it under the terms of the GNU Lesser General Public License as published by the Free Software Foundation; either version 2.1 of the License, or (at your option) any later version. This library is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Lesser General Public License for more details. You should have received a copy of the GNU Lesser General Public License along with this library; if not, write to the Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/sql.py"
        ]
    },
    {
        "copyright": "Copyright (C) 2021 Aswin Murali (aswinmurali.co@gmail.com)",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/Dockerfile"
        ]
    },
    {
        "copyright": "Copyright (C) 2021 Gaurav Mishra <mishra.gaurav@siemens.com>",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/Dockerfile"
        ]
    },
    {
        "copyright": "Copyright (C) 2020 Soham Banerjee (sohambanerjee4abc@hotmail.com),",
        "filePath": [
            "Nirjas-master.zip/Nirjas-master/nirjas/languages/julia.py"
        ]
    }
]

```

The requested URL for getting the response is: `localhost/repo/api/v1/uploads/<UPLOAD_ID>/copyrights`

### 👨‍💻 PR link - [feat(api): new endpoint for geting copyright details](https://github.com/fossology/fossology/pull/2273)

## All jobs only accessible by admin

Made changes in the UI so that only admins can access the `All Recent Jobs` page. For other users the route will not be there in the navigation bar.

Admin veiw:<br/>
![adimin_veiw](/img/reactUI/admin_view.jpeg)

Non-Admin View:<br/>
![non_adimin_veiw](/img/reactUI/non_admin_view.jpeg)

### 👨‍💻 PR link - [feat(ui): All jobs only accessible by admin](https://github.com/fossology/FOSSologyUI/pull/245)

## Clearing Decisions endpoint added and in progress

_(August 14th, 2022)_

Working on the `uploads/<uploadID>/licenses` endpoint to return the latest clearing decision for each and every filepath.

Was able to return the latest clearing status for each upload ID and return it in the api response:

![api_res](/img/reactUI/api_clearing_decision.jpeg)

### 👨‍💻 PR link - [feat(api): clearing status](https://github.com/fossology/fossology/pull/2288)

# License browser page updated

Worked on the License Browser page and formatted the scanner results and the edited results response. Also modified to remove the limit on the page to view all the responses.<br/>
Current status of the License browser page:

![api_res](/img/reactUI/licenses_edited.jpeg)

### 👨‍💻 PR link - [fix(licenses): header fixed and limit for responses removed](https://github.com/fossology/FOSSologyUI/pull/246)

## `uploads/<uploadID>/licenses` endpoint completed

_(August 14th, 2022)_

Working on the `uploads/<uploadID>/licenses` endpoint to return the latest clearing decision for each and every filepath completed this week.
Used `ItemTreeBounds` to get the latest clearing decisions. Rather than using the seperate SQL qureies and modifications in the DAO files created seperate functions so that they can be reused and the funcionality of the earlier funtctions in the DAO files remain the same.

Was able to return the latest clearing status for each upload ID and return it in the api response:

![api_res](/img/reactUI/api_clearing_decision.jpeg)

The new function created in `LicenseDao.php`:

```
public function getLicensesAndTreeIdPerFileNameForAgentId(ItemTreeBounds $itemTreeBounds,
                                                   $selectedAgentIds=null,
                                                   $includeSubfolders=true,
                                                   $excluding='',
                                                   $ignore=false,
                                                   &$clearingDecisionsForLicList = array())
  {
    $uploadTreeTableName = $itemTreeBounds->getUploadTreeTableName();
    $statementName = __METHOD__ . '.' . $uploadTreeTableName;
    $param = array();

    $condition = " (ufile_mode & (1<<28)) = 0";
    if ($includeSubfolders) {
      $param[] = $itemTreeBounds->getLeft();
      $param[] = $itemTreeBounds->getRight();
      $condition .= " AND lft BETWEEN $1 AND $2";
      $statementName .= ".subfolders";
    } else {
      $param[] = $itemTreeBounds->getItemId();
      $condition .= " AND realparent = $1";
    }

    if ('uploadtree_a' == $uploadTreeTableName) {
      $param[] = $itemTreeBounds->getUploadId();
      $condition .= " AND upload_fk=$".count($param);
    }

    $agentSelect = "";
    if ($selectedAgentIds !== null) {
      $statementName .= ".".count($selectedAgentIds)."agents";
      $agentSelect = "WHERE agent_fk IS NULL";
      foreach ($selectedAgentIds as $selectedAgentId) {
        $param[] = $selectedAgentId;
        $agentSelect .= " OR agent_fk = $".count($param);
      }
    }

    $sql = "
SELECT uploadtree_pk, ufile_name, lft, rgt, ufile_mode,
       rf_shortname, agent_fk
FROM (SELECT
        uploadtree_pk, ufile_name,
        lft, rgt, ufile_mode, pfile_fk
      FROM $uploadTreeTableName
      WHERE $condition) AS subselect1
LEFT JOIN (SELECT rf_shortname,pfile_fk,agent_fk
           FROM license_file, license_ref
           WHERE rf_fk = rf_pk) AS subselect2
  ON subselect1.pfile_fk = subselect2.pfile_fk
$agentSelect
ORDER BY lft asc
";

    $this->dbManager->prepare($statementName, $sql);
    $result = $this->dbManager->execute($statementName, $param);
    $licensesPerFileName = array();

    $row = $this->dbManager->fetchArray($result);
    $pathStack = array($row['ufile_name']);
    $rgtStack = array($row['rgt']);
    $lastLft = $row['lft'];
    $path = implode('/', $pathStack);
    $uploadTreeId = $row['uploadtree_pk'];
    $this->addToLicensesAndTreeIdPerFileName($licensesPerFileName, $path, $row, $ignore, $clearingDecisionsForLicList, $uploadTreeId);
    while ($row = $this->dbManager->fetchArray($result)) {
      if (!empty($excluding) && false!==strpos("/$row[ufile_name]/", $excluding)) {
        $lastLft = $row['rgt'] + 1;
        continue;
      }
      if ($row['lft'] < $lastLft) {
        continue;
      }

      $this->updateStackState($pathStack, $rgtStack, $lastLft, $row);
      $path = implode('/', $pathStack);
      $this->addToLicensesAndTreeIdPerFileName($licensesPerFileName, $path, $row, $ignore, $clearingDecisionsForLicList, $uploadTreeId);
    }
    $this->dbManager->freeResult($result);
    return array_reverse($licensesPerFileName);
  }
```

### 👨‍💻 PR link - [feat(api): clearing status](https://github.com/fossology/fossology/pull/2288)

## Download file using UploadID

Developed an API endpoint to send the file as a response for the respective `UploadId`. The Api sends the file with their respective mimetype and file name which can be downloaded in the frontend.<br/>
Current status of the Download API response:

![api_res](/img/reactUI/download_response.png)

### 👨‍💻 PR link - [feat(api): Download file using UploadID](https://github.com/fossology/fossology/pull/2309)

## Fix failing tests due to lint errors

_(September 14th, 2022)_

Worked on finding failing tests and linting issues.

found issues on the file `openapi.yaml` and fixed them

### 👨‍💻 PR link - [fix(lint): openapi lint corrected](https://github.com/fossology/fossology/pull/2311)

## Started with UI integration for clearing status

Started with the implementation of UI for the clearing statuses: 
Currently finished indexing the images as follows:

![index](/img/reactUI/indexing.png)

## Started with UI integration for Download operation for uploaded files

Started with the implementation of UI for the downloading process. The backend for this ready and [merged](https://github.com/fossology/fossology/pull/2309) 


## Documentation:📄

During the GSoC period, I got the time to create and organize documentation for both the [**FOSSology UI**](https://github.com/fossology/FOSSologyUI) and FOSSology [**REST-API**](https://github.com/fossology/fossology). The documentation contains all the user and developer information of the project and is organized in a way to be easily accessible by all.

The weekly documentation of updates can be found at [**FOSSology/gsoc**](https://fossology.github.io/gsoc/docs/2022/ui/updates/soham/2022-06-24)


<h1 align="center">👨🏻‍🏫 DELIVERABLES <img src="https://api.ezeelo.com/Scripts/QRCode/Done.gif" width="40"></h1>

| Tasks   | Planned | Completed     | Remarks    |
| :---:       |    :----:   |    :---:      |    :---:      |
| Adding new pages and improved existing UI   | Yes       | :heavy_check_mark: | The refreshed UI has now a lot of major functionalities but also needs more functions to be implemented and user experience can be improved a lot in the future |
| Adding almost all APIs on GROUPs module , Maintenance and License   | Yes        | :heavy_check_mark:  | More APIs will continously need to be added as the UI Migration progresses |
| Fixing some potential the existing bugs| Yes | :heavy_check_mark: | There're still alot of issues to work on , escpecially on the side of  [FOSSology](https://github.com/fossology/fossology/issues) |
| Fixing Vulnerable FOSSology UI's dependencies| NO (WAS OPTIONAL) | :x: | Dependencies are continously added so this's approgressive task|
| Integrating OAuth 2.0 | NO (WAS OPTIONAL) | :x: | Got the overview still needs more lessons to learn how to integrate it in the existing projects|

## Future enhancements:🚀

- Adding the skeleton loading on the UI components when the items are being fetched.
- Adding search utilities on the select components from the UI.
- Completing to add all the remaining pages on the License Administration Section.
- Adding more REST-APIs from the backend.
- Creating a better User Experience.

## Major Takeaways: 📚

- The project introduced me to develop REST- APIs using Slim framework
- The mentors helped me a lot in understanding the structure of the project.
- Got a lot of experience and help which enhanced my PHP skills.
- Provided me the oppurtunity to work with a brilliant team and hence improved my team skills.
- Got to know about professional coding ethics and how big organisations work.
- Got cool experience on contributing to the opensource projects.
- The last but not least I had a lot of during this entire duration. Learning and having fun was an awesome package.

## Links of work done: 🎯

### Pull Requests 🔗

- [FOSSology](https://github.com/fossology/fossology/pulls?q=is%3Apr+author%3Asoham4abc)
- [FOSSologyUI](https://github.com/fossology/FOSSologyUI/pulls?q=is:pr+author:soham4abc)

# Let's get connected!

- [LinkedIn](https://www.linkedin.com/in/soham-banerjee-6091831b3/)
- [GitHub](https://github.com/soham4abc)
- [Twitter](https://twitter.com/soham4abc)
 



