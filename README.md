Nexus Maven Respository for CloudBees
=====================================

Nexus is a very powerful repository manager for [Maven](http://maven.apache.org/). You can use Nexus to setup and manage the Java artifacts and libaries used by your projects.

The easiest way to setup a Nexus repository is to install deploy it on your CloudBees account.

<a href="https://grandcentral.cloudbees.com/?CB_clickstart=https://raw.github.com/swashbuck1r/sonatype-nexus-clickstart/master/clickstart.json"><img src="https://d3ko533tu1ozfq.cloudfront.net/clickstart/deployInstantly_white.png"/></a>

By default, your Nexus app on CloudBees will be attached to save artifacts in temporary local storage, which means it will be reset any time your application is restarted on CloudBees.  This is useful for testing, but to run a production Nexus instance that can be depended on by your team, you'll need to attach a permanent filestore to your application.

To permanently store files in Nexus, you can associate your app with a filestore attached to your S3 bucket on your own AWS account.

    $ bees resource:create -t s3fs YOUR_RESOURCE_NAME s3_bucket=YOUR_AWS_BUCKET_NAME s3_passwd=YOUR_AWS_KEY:YOUR_AWS_SECRET mount_link=sonatype-work
    $ bees app:bind -a NEXUS_APP_ID -r resource:YOUR_RESOURCE_NAME -as fs-nexus


